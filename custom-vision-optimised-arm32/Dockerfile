﻿FROM balenalib/raspberrypi3:stretch

# Enable cross building of ARM on x64 hardware, Remove this and the cross-build-end if building on ARM hardware.
RUN [ "cross-build-start" ]

# Install dependencies
RUN apt-get update &&  apt-get install -y --no-install-recommends \
        python3 \
        python3-pip \
        build-essential \
        python3-dev \
        libopenjp2-7-dev \
        libtiff5-dev \
        zlib1g-dev \
        libjpeg-dev \
        libatlas-base-dev \
        && rm -rf /var/lib/apt/lists/* \
        && apt-get -y autoremove

# Python dependencies
RUN export PIP_DEFAULT_TIMEOUT=100 
RUN pip3 install --upgrade pip 
RUN pip3 install --upgrade setuptools 
RUN pip3 install pillow numpy flask tensorflow


# Add the application
ADD app /app

# Expose the port
EXPOSE 80
EXPOSE 5679

# Set the working directory
WORKDIR /app

RUN export PYTHONUNBUFFERED=TRUE

# End cross building of ARM on x64 hardware, Remove this and the cross-build-start if building on ARM hardware.
RUN [ "cross-build-end" ]

# Run the flask server for the endpoints
CMD ["python3","app.py"]
