---
layout: post
title: "Semantic DevBlog: Introduction"
---

Semantic DevBlog is a series a blog posts where I aim to document everything related to ideation, design and development of [semanteecore](https://github.com/semanteecore/semanteecore). 

Mainly, it would be useful for me to write things down when I think, and, maybe this will become a somewhat usable "hacking" documentation. In case there are other people who find release automation sexy, of course ;)

### What is `semanteecore`?

<img src="/images/what-if-i-told-you-release-doesnt-have-to-be-painful.jpg" alt="drawing" width="200"/>

`semanteecore` builds on ideas implemented in [semantic-release](https://github.com/semantic-release/semantic-release) (from node.js ecosystem), and extends them. <br>
Implementation-wise `semanteecore` is a successor of `semantic-rs`, an automated crate-publishing tool, originally authored by [schultyy](https://github.com/schultyy) and [badboy](https://github.com/badboy) (thanks a lot!).


For me this project is a reflection of what I personally see as the main part of a perfect release flow: easy to use and almost fully automated.
It’s time consuming to do versioning, changelogs and releases manually as is, and, as project gets bigger, and grows a few sub crates… You get the idea.


And even though every component of `semanteecore` can be expressed in just plain CI configuration file, maintaining those scripts across multiple repositories gets old really fast.


Basically, `semanteecore` an automated toolbox, that speeds up both release process and bootstrapping of new repositories, which at the same time provides a few nice tools like commit-aware changelog generation out of the box, all in a single binary (or docker container).


Since the original implementation (`semantic-rs`), a few changes were made:

#### Features
- Improved and more context-rich spanned logger
- Upload assets for GitHub Releases page
- Support for major-zero versions (thanks, [mandrean](https://github.com/mandrean))
- Configuration through `releaserc.toml` file, akin to `semantic-release`
- `.env` support
- Early Exit if new version is the same as previous (based on semantic commits)
- Docker plugin for building and publishing images to Dockerhub (very alpha, subject to change)
- Support of `Draft` and `Pre-release` GitHub release types
- Integration Testing (only for dry phase for now)

#### Bug Fixes
- Fix crash if the repo is new and had no releases before

#### Internal Changes
- Proof-of-Concept Plugin system

#### Other
- Transition to Rust 2018

### Goals and non-goals of the project
`semanteecore`, as a set of goals, has a moving scope, which is bad, but I didn’t realise how complex a versatile CI tool can become when I started the project. So don’t be surprised if this list looks completely different in half a year ;)  
  
Though I will really try to limit the scope to “releases stuff” only, if it won’t ruin user experience.

Nevertheless, here it goes:

#### Goals

- Automated **semver** versioning via semantic-commits or other custom conventions (e.g. YouTrack tasks and their categories) 
- Multi-platform preparation, checking and publishing of a release
- Rich and easy to use **plugin system**, that provides deterministic communication layer between plugins. That allows to combine plugins and build pipelines of them, through a shared key-value storage.
- Native **mono-repository support** (e.g. Cargo Workspace)

#### Non-Goals

- Anything related to deployment, though post-release notification stage is a supported use case for plugins, and that could be used to send an event to your deployment system.

#### Thank you for reading!

This is the first blog post in a series. Stay tuned!