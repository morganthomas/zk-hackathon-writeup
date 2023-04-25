# Nixing zk-Harness

This work was done with the support of Casper Association.

For my contribution to the [Berkeley RDI ZKP / Web3 Hackathon, 2023](https://zk-hacking.org/), I made a Nix environment for the [zk-Harness](https://github.com/zkCollective/zk-Harness/) benchmarking framework and suite of benchmarks. The Nix environment allows for the benchmarks to be compiled, developed, and run on any Nix-compatible system. It pins the dependency versions, so that different versions of dependencies in the environment should not affect the results.

This suite is a particularly good use case for Nix, because it has a large dependency footprint which can only be expected to grow as more frameworks are added. The main benefit is that it saves the user of the suite from needing to go through a lengthy setup process in order to compile, develop, and run the benchmarks on their machine.

Building this Nix environment required creating Nix build code for Circom and Gnark. The more problematic aspect of building this Nix environment was pulling in the Node.js and Python dependencies. Node.js and Python packages can be difficult to integrate into Nix in a Nixy way. Node.js and Python have their own package management systems. The functionality of those package management systems has to be replicated in Nix in order to manage dependencies directly with Nix. I considered [dream2nix](https://github.com/nix-community/dream2nix) as a solution for managing Node.js and Python dependencies, but ultimately settled on pulling in the Node.js and Python runtimes and package management systems using Nix and running their dependency installation processes in the Nix development shell setup process.
