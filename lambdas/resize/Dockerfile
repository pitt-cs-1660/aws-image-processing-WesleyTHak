FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

# set working directory
WORKDIR /var/task

# copy dependency definition
COPY pyproject.toml .

# install dependencies into .venv
RUN uv sync --frozen --no-dev

# copy handler code
COPY handler.py .

# point Python to the uv environment
ENV PYTHONPATH=/var/task/.venv/lib/python3.13/site-packages

# Lambda entrypoint
CMD ["handler.resize_handler"]
