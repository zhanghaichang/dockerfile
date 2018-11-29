# dockerfile


```
# uid (-u) and group IDs (-g) are fixed to 1000 to be used for development
# purposes
# FIXME: 1000 change this number for your linux number ID ($ id -u $USER where $USER is your linux
# user name)
RUN useradd -u 1000 -md /home/rootuser -ms /bin/bash -G builder,sudo rootuser \
    && echo "rootuser:docker" | chpasswd \
    && echo "rootuser ALL=(ALL) NOPASSWD:ALL" >> /etc/sudoers
```
