To get the code

```bash
git clone https://github.com/ggerganov/llama.cpp
cd llama.cpp
sudo pacman -Sy cuda cuda-tools
cmake -B build -DGGML_CUDA=ON
cmake --build build --config Release

```
