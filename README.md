# immich-photos

Configuration and code repository for Immich photo library.

## Overview

This repository contains configuration files and code for managing the Immich photo library. The actual media files (photos, videos, thumbnails) are stored locally and excluded from version control via `.gitignore`.

## Directory Structure

- `backups/` - Photo backups (excluded from git)
- `library/` - Main photo library (excluded from git)
- `thumbs/` - Thumbnail cache (excluded from git)
- `encoded-video/` - Encoded video files (excluded from git)
- `upload/` - Upload directory (excluded from git)
- `profile/` - Profile images (excluded from git)

## Setup

This directory is used by Immich running in Docker. The media directories are mounted as volumes in the Immich container.

## Self-Hosting Stack

- **Domain**: stephen8n.com
- **Platform**: Docker
- **Services**: Immich, n8n
