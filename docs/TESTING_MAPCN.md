# Testing MapCN/Carto Integration

This guide helps verify that the MapCN integration works correctly.

## Prerequisites

- Node.js >= 20
- pnpm installed
- Running data synced (or sample data)

## Quick Test (5 minutes)

1. Clone the repository and checkout the PR branch.
2. Install dependencies:
   ```bash
   pnpm install
   ```
3. Start development server:
   ```bash
   pnpm develop
   ```
4. Open http://localhost:5173 in your browser.

## Testing Checklist

### ✅ Basic Functionality
- [ ] Map tiles load without errors.
- [ ] Map displays at correct initial position.
- [ ] No console errors in browser DevTools.
- [ ] No 404 or network errors in Network tab.

### ✅ Visual Quality
- [ ] Map tiles are clear and readable.
- [ ] Text labels are visible.
- [ ] Colors match the theme (light/dark).
- [ ] Map looks professional.

### ✅ Running Routes
- [ ] Running route polylines display correctly.
- [ ] Routes follow actual paths (not straight lines).
- [ ] Multiple routes display without overlap issues.
- [ ] Route colors are visible against map background.

### ✅ Theme Switching
- [ ] **Light theme:** Map uses `osm-bright` (Voyager) style.
- [ ] **Dark theme:** Map uses `dark-matter` style.
- [ ] Switching themes updates map immediately.
- [ ] No visual glitches during theme transition.

### ✅ Map Controls
- [ ] Zoom in/out buttons work.
- [ ] Zoom with scroll wheel works.
- [ ] Pan/drag map works.
- [ ] Fullscreen control works.
- [ ] "Lights" control works (privacy mode).

### ✅ Performance
- [ ] Map loads in < 5 seconds on normal connection.
- [ ] Zoom/pan is smooth (no lag).
- [ ] Works well with many routes displayed.

### ✅ Responsive Design
- [ ] Map displays correctly on mobile screens.
- [ ] Touch gestures work (pinch zoom, drag).
- [ ] Controls are accessible on small screens.

### ✅ Chinese Language Support (if IS_CHINESE = true)
- [ ] Map labels show Chinese characters (where available in basemap data).
- [ ] Chinese location names display correctly.

### ✅ Backward Compatibility
Test switching back to other providers:

**Test Mapbox:**
Modify `src/utils/const.ts`:
```typescript
export const MAP_TILE_VENDOR = 'mapbox';
export const MAP_TILE_STYLE_LIGHT = 'light-v10';
export const MAP_TILE_STYLE_DARK = 'dark-v10';
export const MAP_TILE_ACCESS_TOKEN = 'your_mapbox_token';
```
- [ ] Mapbox works correctly.

**Test MapTiler:**
Modify `src/utils/const.ts`:
```typescript
export const MAP_TILE_VENDOR = 'maptiler';
export const MAP_TILE_STYLE_LIGHT = 'basic-light';
export const MAP_TILE_STYLE_DARK = 'basic-dark';
export const MAP_TILE_ACCESS_TOKEN = 'your_maptiler_token';
```
- [ ] MapTiler works correctly.

## China-Specific Testing
If testing from China:
- [ ] Map tiles load (not blocked by firewall).
- [ ] Loading speed is acceptable.
- [ ] No timeout errors.

**Note:** If Carto is blocked, check if `MAP_TILE_FALLBACK_PROVIDERS` are configured and working.
