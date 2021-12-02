FROM python:3.9.9-slim-bullseye

LABEL org.opencontainers.image.authors="mathieu@mathieulemieux.com"

# RUN groupadd --gid $GID $GROUPNAME
# RUN useradd --uid $UID --gid $GID -m $USERNAME


# ARG USERNAME=mathieu
# ARG USER_UID=1000
# ARG USER_GID=$USER_UID

# # Create the user
# RUN groupadd --gid $USER_GID $USERNAME \
#   && useradd --uid $USER_UID --gid $USER_GID -m $USERNAME \
#   && apt-get update \
#   && apt-get install -y sudo \
#   && echo $USERNAME ALL=\(root\) NOPASSWD:ALL > /etc/sudoers.d/$USERNAME \
#   && chmod 0440 /etc/sudoers.d/$USERNAME

# # [Optional] Set the default user. Omit if you want to keep the default as root.
# USER $USERNAME

# ENV USER=root

RUN python3 -m pip install --upgrade pip

COPY ./requirements.txt /app/requirements.txt

RUN pip install -r /app/requirements.txt

COPY ./app /app

WORKDIR /app

CMD [ "uvicorn", "main:app", "--host", "0.0.0.0", "--reload" ]