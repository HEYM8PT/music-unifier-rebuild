# Phase 1: Search + Download

## Goal
Allow users to search any artist/track/album, see results from both Navidrome (what they own) and Tidal (what they can download), and download from Tidal with one tap.

## Current State (What Exists)
- TV search screen (TvSearchScreen.kt) has 4 tabs: Albums, Songs, Artists, Tidal
- TV shows Tidal results with TidalResultCard + download button + progress
- SongsScreen shows inline search with Tidal results below Navidrome results
- SongsScreenViewModel has search(), downloadTidalTrack(), getDownloadStateForTrack()
- Middleware has: /api/search (unified), /api/download-status/:id, /api/downloads
- TidalResultCard composable exists
- Screens that DON'T have Tidal: AlbumScreen, ArtistScreen

## What Needs to Change

### 1. Dedicated Phone Search Screen (like TV)
- New SearchScreen.kt with tabs: Albums | Songs | Artists | Tidal
- Each tab queries its respective source
- Tidal tab shows results with download buttons

### 2. Add Tidal to Album + Artist Search
- AlbumScreen search should also show Tidal album results
- ArtistScreen search should show Tidal artist results  
- Download button on each

### 3. Search Navigation
- Add search icon to bottom nav bar
- Wire navigation to new SearchScreen

### 4. Download UX
- Show download progress in the results
- Show quality badges on Tidal tracks
- Notification when download completes

## Middleware Endpoints (Already Working)
- GET /api/search?q=artist+track → unified search
- GET /api/download-status/:id → check download status
- GET /api/downloads → list all downloads
- POST /api/playlists/generate → generate playlists

## Files to Modify
| File | Change |
|------|--------|
| New: SearchScreen.kt | Full search screen with tabs |
| Screen.kt | Add Search + SearchTidal routes |
| NavGraph.kt | Add composable routes |
| AlbumScreen.kt | Add Tidal section to search |
| ArtistScreen.kt | Add Tidal section to search |
| SongsScreen.kt | Already has Tidal, minor polish |
| MiddlewareClient.kt | Add search methods if missing |

## Build Command
```bash
export DOCKER_CONFIG=/DATA/.docker
docker --config $DOCKER_CONFIG run --rm \
  -v /DATA/AppData/openclaw/workspace/projects/music-unifier/app:/app \
  -v /opt/android-sdk:/opt/android-sdk \
  eclipse-temurin:21 \
  bash -c "export ANDROID_HOME=/opt/android-sdk && cd /app && ./gradlew assembleDebug --no-daemon 2>&1 | tail -5"
```
