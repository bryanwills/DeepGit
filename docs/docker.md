<h1 align="center">
  <img src="https://img.icons8.com/?size=100&id=118557&format=png&color=000000" width="72" style="vertical-align: middle;"/> DeepGit on Docker
</h1>

Build the Docker Image
From the root directory of your project, run:

```bash
docker build -t deepgit-app .
```

This command builds a Docker image tagged as deepgit-app using Python 3.10-slim as the base image and installs all the necessary dependencies.

### Run the Docker Container
Once the image is built, start a container with:

```bash
docker run -p 7860:7860 deepgit-app
```
This command maps port 7860 from the container to your local machine, allowing you to access the Gradio interface of DeepGit in your web browser.

### Important: Gradio Port Binding Fix

Ensure that your app.py file includes the following line to allow external access from Docker:

```bash
demo.queue(max_size=10).launch(server_name="0.0.0.0", server_port=7860)
```

Without this fix, Gradio will bind to localhost inside the container, making it inaccessible from your browser.

