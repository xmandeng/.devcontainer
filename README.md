# Instructions

In your VS Code project, create a subfolder called `.devcontainer` and copy the `Dockerfile` and `devcontainer.json` files.

## Ollama
1. Build the devcontainer as usual.
2. In the terminal, run:
    ```sh
    ollama server
    ```
3. Open another terminal (suggest splitting) and run:
    ```sh
    nvtop
    ```
4. In a third terminal, run:
    ```sh
    ollama run <your model>
    ```

## Stable Diffusion WebUI Forge
1. Clone the application repository
   ```sh
   git clone git@github.com:lllyasviel/stable-diffusion-webui-forge.git
   ```
2. Build the devcontainer as usual. 
3. Run:
    ```sh
    ./webui.sh
    ```
4. Install the CivitAI extension.
5. Download and install checkpoints.
