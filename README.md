This repository contains a minimal example of a problem between ts_library and rollup_bundle i've been having.

# Setup

`lib` contains a minimal typescript library in its `src` directory and has a `BUILD.bazel` file mapping the `src` folder as `module_root` under `module_name` `kevin`.

`lib_root` contains the same library as `lib` but not inside of a `src` folder.

`app` contains a minimal `rollup.config.js` and a `index.ts` file using the `kevin` function from the `kevin` library with a `bundle` target in its `BUILD.bazel` file that runs the `rollup_bundle` step.

# Problems

when building the `bundle` in the current configuration the `ts_library` step completes successfully but during bundling the `kevin` library cannot be found while the `kevin_root` library resolves successfully.

Moving the `index.ts` file to the root of the `lib` package and updating the `BUILD.bazel` file to reflect those changes allows for proper compilation, which leads me to suspect some problem in the `module_root` mapping.