# Bio
Hi! My name is Zahir and I'm a senior at Bennington College. This repository is a record of my work in the Open Source Contribution class, for Fall 2024, with faculty instructor, [Michael Corey](https://www.bennington.edu/academics/faculty/michael-corey). This class was a wonderful opportunity to learn about open source contribution and good 
practices. As our teacher says, programming is a collaborative discipline, and this class has given me a great deal of experience collaborating on code with others.
- My LinkedIn can be found [here](https://www.linkedin.com/in/zahirsabotic).
- My GitHub can be found [here](https://github.com/zahirsabotic).


# List of Solo Fixes
'm' next to the pull request means it was merged
List your solo fixes with a brief (1 line) descriptor of what you did:

- degree centrality feature for RustworkX: PR [#1306](https://github.com/Qiskit/rustworkx/pull/1306) (m)
- wash get links error handling: PR [#3621](https://github.com/wasmCloud/wasmCloud/pull/3621) (m)
- wash deploy error [#3621](https://github.com/wasmCloud/wasmCloud/pull/3621) (m)
- bind multiple http paths with fallback: PR (Kinode) [#119](https://github.com/kinode-dao/process_lib/pull/119)
- 

# Group Fix
For this group fix, I worked with Ons, Malik, and Michael to add degree centrality support to the rustworkx library. I personally found joy in being able to take the lead on this project, as I was the one with most experience in Rust, so we were able to parse the codebase and understand the necessary changes. This PR only included basic function and and the bindings, and I later added in-degree and out-degree centrality support to the library.
- Group fix: degree centrality feature for RustworkX: PR [#1306](https://github.com/Qiskit/rustworkx/pull/1306)

# Essay
[Link to Essay](https://docs.google.com/document/d/1vyqvrG-7-fiwhzg36-eQF5HVtHpQ3sHl5U4gwhsGZ04/edit?usp=sharing)

# Learnings
A brief (apx. 500 words) about what you learned in the course, your major pain points, and anything you wish you learned more about. 
This course was a wonderful opportunity to develop professionally in an academic setting: open source contribution is a proven, malleable action step one can take to advance their professional track record (and is much more fun than Leetcode anyways). Due to my current job, most of my professional experience right now is in blockchain development, and this course enabled me to strike a balance between the job and other domains of software development. Due to the nature of the company I work at (and the industry), I often feel like I miss out on some standard practices of general software engineering. In the light of that, I tried to align my interests (and work to do by extension) with some more common patterns in development (CLI tools, for example). Overmore, I contributed to RustworkX based on my interest in language-to-language support (and the Rust-Python bindings), and I contributed to the WASM project based on my interests in polyglot app development. I would say that my work in this class aligned with interests in multi-language app development: programming languages are opinionated for a reason (each one serves their intended purposes really well), so there is important work to be done in aligning these technologies to work together.

One domain-agnostic learning achievement was getting more comfortable with git (and Github for the matter) and the whole PR workflow. git has shown to be a pain point sometimes over the course (and at my job), so it was rewarding to notice progress and to independently solve git issues. I would say overall that I am much more comfortable with the workflow of submitting a PR, iterating on it, and getting it to a place where it is merged into main. It is much clearer now that a PR is not a mere change in logic, but is rather a multifaceted process involving back-and-forth communication, writing out documentation, release documents, and tests (stuff I have naively done in the past). 

Overall, this class has made me a better engineer. While I have got good experience at my current job, the class has exposed me to a breadth of patterns in software development which I have not seen before. This has most to do with API design, and how there are often clear patterns to how an API is developed, even across codebases. Nevertheless, the more bugs I tried to fix, the merrier I felt when approaching the next one. Overall, I am very happy with my work in the class, and are left with the feeling that I should’ve done more (and I intend to in the future).
