# TQD Website

A Hugo-based static website built with the Congo theme.

## Prerequisites

- Git
- Hugo Extended v0.148.1
- Podman (or Docker) (optional)

## Install Prereqs

### 1. Clone the Repository

```bash
git clone https://github.com/thequietdisconnect/website.git
cd tqd-website
```

### 2. Initialize Submodules

This project uses Git submodules for the Hugo theme. Initialize them recursively:

```bash
git submodule update --init --recursive
```

### 3. Install Hugo Extended

#### Debian/Ubuntu

```bash
# Download Hugo Extended v0.148.1 .deb package
wget https://github.com/gohugoio/hugo/releases/download/v0.148.1/hugo_extended_0.148.1_linux-amd64.deb

# Install the package
sudo dpkg -i hugo_extended_0.148.1_linux-amd64.deb

# Verify installation
hugo version
```

> **Note:** For installation instructions on other operating systems, see the [official Hugo installation documentation](https://gohugo.io/installation/).

## Building the Site

### Generate Static Files

Build the site and generate the `public/` directory:

```bash
hugo
```

This will compile all content and generate static HTML files in the `public/` directory.

### Development Server

For local development with live reload:

```bash
hugo server -D
```

Visit `http://localhost:1313` to view the site.

## (Optional) Serve Files with Podman

### Run with Nginx

Serve the built site using Nginx in a Podman container:

```bash
podman run --rm -d \
  --name tqd-website \
  -p 8080:80 \
  -v ./public:/usr/share/nginx/html:ro \
  nginx:stable
```

The site will be available at `http://localhost:8080`

### Re-build and Update
To update the site after making changes, rebuild it:

```bash
hugo
```

### Stop the Container

```bash
podman stop tqd-website
```
