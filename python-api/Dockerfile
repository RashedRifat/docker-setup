# Base Image 
FROM python:3.9

ENV PYTHONUNBUFFERED 1
ENV WORKDIR="/app"
ENV PATH="${PATH}:/root/.local/bin"

# Update 
RUN apt-get update \
    && apt-get install --no-install-recommends -y \
    curl \
    build-essential
RUN python3 -m pip install --upgrade pip

# Generate Workdir 
RUN mkdir -p ${WORKDIR}
WORKDIR ${WORKDIR}

# Install the project using Poetry 
RUN curl -sSL https://install.python-poetry.org | python3 - 
RUN echo "export PATH=\$PATH:\$HOME/.local/bin" >> /root/.bashrc
RUN echo "alias ls='ls -la'" >> /root/.bashrc

# Copy over the poetry files
COPY poetry.lock pyproject.toml ./
RUN poetry config virtualenvs.create false
RUN poetry install --no-dev

# Expose ports 
EXPOSE 5000

# Bash Setup 
RUN sed -i "s/# export LS_OPTIONS/export LS_OPTIONS/" /root/.bashrc

# Start the command terminal 
CMD /bin/bash