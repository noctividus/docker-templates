FROM golang:1.20

# Install system dependencies
RUN apt-get update && apt-get install -y \
    git \
    systemd \
    && rm -rf /var/lib/apt/lists/*

# Set the working directory
WORKDIR /app

# Clone and build the application
RUN git clone https://github.com/mafredri/lcm.git . \
    && go build ./cmd/openlcmd \
    && cp openlcmd /usr/local/sbin/openlcmd

# Copy and enable systemd service
RUN cp cmd/openlcmd/systemd/openlcmd.service /etc/systemd/system/openlcmd.service \
    && systemctl enable openlcmd

# Expose device
VOLUME ["/dev/ttyS1"]

# Start systemd
CMD ["/usr/sbin/init"]