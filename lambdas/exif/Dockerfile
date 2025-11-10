FROM public.ecr.aws/lambda/python:3.13

# install uv
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

WORKDIR /var/task

COPY pyproject.toml .

RUN uv sync --frozen --no-dev

COPY handler.py .

ENV PYTHONPATH=/var/task/.venv/lib/python3.13/site-packages

CMD ["handler.exif_handler"]
