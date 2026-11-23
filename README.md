# canvasforge-engine

Ready-made builds of `sd-server` from [stable-diffusion.cpp](https://github.com/leejet/stable-diffusion.cpp)
(MIT license) for Linux with CUDA 12, built unmodified from a pinned commit.

The upstream project publishes Windows and macOS builds but no Linux CUDA build. Compiling one on a rented
GPU session takes many minutes; downloading one takes seconds.

- Each release is named `engine-<upstream tag>` and holds `sd-server-linux-cuda12.tar.gz` and its SHA-256.
- The build recipe is `.github/workflows/engine-linux-cuda.yml`. It fetches the exact upstream commit, builds
  it with CUDA for the T4, A100, L4 and H100 generations, and publishes the result. Nothing is patched.
- Built on Ubuntu 22.04 with CUDA 12.4. The machine that runs it needs an NVIDIA driver and the CUDA 12
  runtime libraries.

The license of the engine is in each archive and in `LICENSE-stable-diffusion.cpp` upstream.

Each archive also carries the CUDA 12 runtime libraries the engine needs (cuBLAS and the CUDA runtime, in `lib/`,
redistributed under the NVIDIA CUDA EULA included there), so the engine does not depend on the CUDA version of the
machine that runs it. That machine needs only an NVIDIA driver.
