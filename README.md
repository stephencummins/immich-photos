# immich-photos

Self-hosted Immich photo management system configuration and media storage.

## Overview

This repository contains Docker configuration files for running Immich, a self-hosted photo and video management solution. The actual media files (photos, videos, thumbnails) are stored locally and excluded from version control.

## Directory Structure

**Configuration Files:**
- `docker-compose.yml` - Main Immich Docker Compose configuration
- `docker-compose-official.yml` - Official reference configuration
- `example.env` - Environment variable template

**Media Directories (excluded from git):**
- `backups/` - Photo backups
- `library/` - Main photo library
- `thumbs/` - Thumbnail cache
- `encoded-video/` - Encoded video files
- `upload/` - Upload directory
- `profile/` - Profile images
- `postgres/` - PostgreSQL database data

## Setup

### 1. Environment Configuration

Copy the example environment file and configure:

```bash
cp example.env .env
# Edit .env with your settings
```

Required environment variables:
- `UPLOAD_LOCATION` - Path to photo library (e.g., `/Users/client/immich-photos`)
- `DB_DATA_LOCATION` - Path to database storage
- `DB_PASSWORD` - PostgreSQL password
- `DB_USERNAME` - PostgreSQL username
- `DB_DATABASE_NAME` - Database name
- `IMMICH_VERSION` - Immich version (default: `release`)

### 2. Start Immich

```bash
docker-compose up -d
```

### 3. Access Immich

- Web interface: http://localhost:2283
- Or via domain: https://stephen8n.com (if configured)

## Self-Hosting Stack

- **Domain**: stephen8n.com
- **Platform**: Docker
- **Services**: Immich, n8n
- **Photo Storage**: Local filesystem
- **Database**: PostgreSQL (in Docker)
- **Cache**: Redis/Valkey (in Docker)

## Backup Strategy

The media files are stored locally and excluded from Git. For backup:
1. Media files: Use rsync, rclone, or similar to backup the `library/` directory
2. Database: Backup the `postgres/` directory or use PostgreSQL dump
3. Configuration: This Git repository backs up all config files

## Migrating from External Services

This setup replaces:
- ❌ Supabase → ✅ Self-hosted PostgreSQL
- ❌ Cloud storage → ✅ Local storage with Immich
- ❌ External hosting → ✅ Self-hosted on stephen8n.com

## Updating Immich

```bash
# Pull latest images
docker-compose pull

# Restart services
docker-compose up -d
```

## Resources

- [Immich Documentation](https://docs.immich.app)
- [Immich GitHub](https://github.com/immich-app/immich)
