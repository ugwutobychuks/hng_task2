# Use an official Python runtime as a parent image
FROM python:3.11-slim

# Set environment variables
ENV PYTHONUNBUFFERED=1
ENV PATH=/root/.local/bin:$PATH

# Set the working directory
WORKDIR /app

# Install pipx and poetry
RUN pip install --user pipx && \
    /root/.local/bin/pipx ensurepath && \
    /root/.local/bin/pipx install poetry

# Install the poetry-plugin-export plugin
RUN /root/.local/bin/pipx inject poetry poetry-plugin-export

# Copy the project files to the Docker image
COPY . /app

# Export the requirements.txt file from Poetry
RUN /root/.local/bin/poetry export -f requirements.txt --output requirements.txt

# Install the dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose the port the app runs on
EXPOSE 8000

# Run the app
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
