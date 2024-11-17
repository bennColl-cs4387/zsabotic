# Solo Fix Progress Report (Week-12)
*Author: Zahir Sabotic*  
*Date: 11/17/2024*

## Project: [wasmCloud](https://github.com/wasmCloud/wasmCloud)
&rarr; **Issue**: wash get links output is inconsistent ([Issue #3548](https://github.com/wasmCloud/wasmCloud/issues/3584)).  
&rarr; **Goal**: Fix the rendering issue with the `wash get links` command.

## Pull Request
[PR #3621](https://github.com/wasmCloud/wasmCloud/pull/3621)


## Discussion
- For this week, my goal was to branch out and work on a new project. I have prior experience with WASM from my work at Kinode so I thought this wasmCloud might be a good project to work on. 

 wasmCloud is a platform for building applications using WebAssembly (WASM) technology. It provides a runtime environment for running WASM modules and a set of tools these modules. 

This issue was described as a CLI rendering issue with the `wash get links` command. The project is large and contains many modules, so I thought for my first pass I would take a look at the `wash-cli` crate.

I have had some experience with Rust CLI programs (thank you Rust Class!), so I thought I would be able to jump right in and parse the codebase. The CLI program itself is a large module, so I had to spend some time trying to narrow in where the troublesome `wash get links` command was located, which was in the following file: 
 `crates/wash-cli/src/common/get_cmd.rs` 

 Now, after spending some time trying to parse the flow of this command, I noticed that the spinner (the little dots that appear on CLI tools to signal loading) was not being handled properly. In particular, the spinner was being defined twice, and only cleared out once, leaving a trailing dot to sometimes render. 

 To that point, I took some time to refactor the code so that no function signature changes happen, and I separated out the spinner logic to be handled according to the match statement. In that way, I did not have to modify the `handle_link_command` function, since it already held the logic for handling the spinner correctly.


## Consideration
While the fix was trivial (and almost obvious when considering the logic changes), I did have to spend some time trying to understand the flow of the code. I think this is  great engineering practice, so I thought that I will look into another issue, and spend time further understanding the codebase.


## Overview of the next bug to fix
The next issue I plan on looking into is the following: [Issue #3034](https://github.com/wasmCloud/wasmCloud/issues/3034). This issue deals with deploying a module to a wasmCloud "lattice" (the runtime environment for running WASM modules). The `wash deploy` command was not working as expected (it does not check whether the component exists before deploying).

I identified `crates/wash-cli/src/app/mod.rs` as the file containing the logic for the `wash deploy` command, in particular:

```rust
async fn deploy_model(cmd: DeployCommand) -> Result<CommandOutput> {
    let connection_opts =
        <CliConnectionOpts as TryInto<WashConnectionOptions>>::try_into(cmd.opts)?;
    let lattice = Some(connection_opts.get_lattice());

    let client = connection_opts.into_nats_client().await?;

    let app_manifest = match cmd.app_name {
        Some(source) => load_app_manifest(source.parse()?).await?,
        None => load_app_manifest("-".parse()?).await?,
    };

    // If --replace was specified, we should attempt to replace the resources by deleting them beforehand
    if cmd.replace {
        if let (Some(name), version) = (
            app_manifest.name(),
            app_manifest.version().map(ToString::to_string),
        ) {
            if let Err(e) =
                wash_lib::app::delete_model_version(&client, lattice.clone(), name, version).await
            {
                eprintln!("🟨 Failed to delete model during replace operation: {e}");
            }
        }
    }

    deploy_model_from_manifest(&client, lattice, app_manifest, cmd.version).await
}`

A check needs to be added to the `app_manifest` to check if the component exists before deploying.


