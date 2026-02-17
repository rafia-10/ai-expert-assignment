# AI Training Software Engineer Assignment

This repository contains the Python assignment for the AI Training Software Engineer role. It includes:

- Application code in `app/`
- Test suite in `tests/`
- Docker setup for CI-style testing
- Bug fix explanation in `Explanation.md`

---

## Running Tests

### 1. Run Tests Locally
    1. Create a virtual environment (optional but recommended):

        ```bash
        python -m venv venv
        source venv/bin/activate  # On Windows: venv\Scripts\activate
`

    2. Install dependencies:

    ```bash
    pip install -r requirements.txt

    3. Run the tests:

    ```bash
    pytest -v

    All tests should run and show detailed output.


    
### 2. Run Tests Using Docker

Build the Docker image:

```bash
docker build -t ai-assignment .


Run the tests inside the container:

```bash
docker run --rm ai-assignment



The container runs pytest -v by default as defined in the Dockerfile.

--rm automatically cleans up the container after tests finish.