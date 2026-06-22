# Small Large Language Model (sLLM)

[![CI](../../actions/workflows/ci.yaml/badge.svg)](../../actions/workflows/ci.yaml)

A Nix template for running a Small Large Language Model (sLLM).

## Get Started

To get started with the project, follow these steps:

1. **Clone the repository:**

   ```bash
   git clone https://github.com/stefankuehnel/sllm.git
   cd sllm
   ```

2. **Open the Dev Container:**

   Open the project in [Visual Studio Code](https://code.visualstudio.com/) and reopen it in the Dev Container when prompted. This starts the `llama-server` service and provisions the Nix `devEnvironment` automatically.

3. **Run the project:**

   ```bash
   task run
   ```

4. **See the response:**

   The task sends a prompt to the model and prints the completion. The `llama-server` API is available at `http://localhost:8080`.

## Usage

This project serves a local small LLM via [llama.cpp](https://github.com/ggml-org/llama.cpp)'s `llama-server`, which exposes an OpenAI-compatible API on port `8080`.

### Sending a prompt

1. **Run the default prompt:**
   - Run `task run` to send the default prompt (`Say hello`) to the model.

2. **Send a custom prompt:**
   - Set the `LLAMA_CPP__PROMPT` environment variable to override the prompt:

     ```bash
     LLAMA_CPP__PROMPT="Explain Nix flakes in one sentence." task run
     ```

### Changing the model

1. **Pick a model:**
   - Update `LLAMA_ARG_HF_REPO` and `LLAMA_ARG_HF_FILE` in `.devcontainer/compose.yaml` (and `.github/workflows/ci.yaml`) to point at a different [GGUF](https://huggingface.co/models?library=gguf) model.

2. **Restart the server:**
   - Rebuild the Dev Container so `llama-server` picks up the new model. Downloaded models are cached in `.llama/models` and survive container rebuilds.

## Development

This project uses [Task](https://taskfile.dev) as a task runner.

### Available Tasks

```bash
# Run the default task (run)
task

# Run project
task run

# Format code
task format

# Clean project artifacts
task clean
```

## Documentation

Below you will find a list of documentation for tools used in this project.

- **llama.cpp**: LLM Inference in C/C++ - [Docs](https://github.com/ggml-org/llama.cpp/tree/master/tools/server)
- **Nix**: Nix Package Manager - [Docs](https://wiki.nixos.org/wiki/Nix)
- **Nix Flakes**: An Experimental Feature for Managing Dependencies of Nix Projects - [Docs](https://wiki.nixos.org/wiki/Flakes)
- **Task**: A Task Runner / Build Tool written in Go - [Docs](https://taskfile.dev/)
- **GitHub Actions**: Automation and Execution of Software Development Workflows - [Docs](https://docs.github.com/en/actions)

## Found a Bug?

Thank you for your message! Please fill out a [bug report](../../issues/new?assignees=&labels=&template=bug_report.md&title=).

## License

This project is licensed under the [GNU General Public License](https://www.gnu.org/licenses/gpl-3.0.txt).
