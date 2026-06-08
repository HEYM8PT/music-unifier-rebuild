# Music Unifier — Rebuild Tracker

Tracking the complete rebuild of the Music Unifier Android app focused on actual user-visible features.

## Phase Status

### Phase 1: Search + Download 🎯
- [ ] 1.1 Dedicated phone search screen with tabs
- [ ] 1.2 Tidal search results + download on phone
- [ ] 1.3 Quality info on search results
- [ ] 1.4 Download progress tracking
- [ ] 1.5 Album + Artist search with Tidal

### Phase 2: Home Screen 🏠
- [ ] 2.1 Fix data loading (done)
- [ ] 2.2 Recommendations with album art
- [ ] 2.3 Smart playlists as cards
- [ ] 2.4 Mood mixes as tiles
- [ ] 2.5 Recently played rendering
- [ ] 2.6 Album art everywhere

### Phase 3: Visual Theme 🎨
- [ ] 3.1 Quality badges visible
- [ ] 3.2 Floating mini player
- [ ] 3.3 Tidal preset works
- [ ] 3.4 AMOLED dark theme
- [ ] 3.5 Bottom nav customization
- [ ] 3.6 Now playing config applies

### Phase 4: Polish 🚀
- [ ] 4.1 Layout presets wired
- [ ] 4.2 CSS theme engine
- [ ] 4.3 Per-row controls
- [ ] 4.4 Performance optimization

## Build Pipeline
```bash
docker run --rm \
  -v $(pwd):/app \
  -v /opt/android-sdk:/opt/android-sdk \
  eclipse-temurin:21 \
  bash -c "export ANDROID_HOME=/opt/android-sdk && cd /app && ./gradlew assembleDebug --no-daemon"
```
