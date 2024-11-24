Update for this week:
Fix is on PR [deployment-fix](https://github.com/wasmCloud/wasmCloud/pull/3682)

Notes:
For this fix, it was first important to understand the subject matter of the bug:
- `wash app deploy` had ambiguous handling of the `deploy` subcommand, more particularly when it came to ingesting the YAML (means 'yet another markup language' for the curious reader), which is the format that dictates how to serve the WASM component. The current configuration does not handle the case where we want to use a local build of the WASM component, as opposed to a remote build.

I didn't want to mess with the API, so I decided to go for a simpler solution, which was to modify the `deploy`, in particular how the manifest is handled. Due to my own-shortcomings in understanding the codebase, I was trying to reproduce the bug, but failed to change the YAML file in a way that would trigger the bug. I ended up identifying the issue and was able to replicate the bug, and then fix it accordingly. The repository mentiones some special handling conditions (when sourcing it from a relative path as opposed to an absolute path), so I will make a pull request WIP to talk with the team about it. 

On that note, I also realized that, when making the pull request, that I accidentally included the commits from my prior fix. The issue was that the commits were rolling over since I did the fix on the 'main' branch, so repository history was being included in the pull request. I managed to fix it by reseting the branches upstream to be the main WasmCloud repository (I stashed the prior fixing commit and just reapplied it after resetting the branch).
