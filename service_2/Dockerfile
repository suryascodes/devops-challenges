FROM python:3.13.5-slim

# Install pipx and uv
RUN pip install uv
WORKDIR /app

# Copy your Python requirements/configuration files
COPY pyproject.toml poetry.lock* requirements.txt* requirements.in* ./

# Install dependencies using uv
RUN if [ -f "pyproject.toml" ]; then \
        uv pip install -r requirements.txt || true; \
        uv pip install . || true; \
    elif [ -f "requirements.txt" ]; then \
        uv pip install -r requirements.txt; \
    elif [ -f "requirements.in" ]; then \
        uv pip install -r requirements.in; \
    fi

COPY requirements.txt .
RUN uv pip install --system -r requirements.txt


# Copy the rest of your application code
COPY . .

EXPOSE 8002

# Set the entrypoint (update "app:main" as needed)
CMD ["python", "app.py"]