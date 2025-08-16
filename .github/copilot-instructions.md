# Mapa FCU (Favelas e Comunidades Urbanas)

**Always reference these instructions first and fallback to search or bash commands only when you encounter unexpected information that does not match the info here.**

This is a static web mapping application that displays municipalities of São Paulo state and overlays data for favelas and urban communities (FCU) using Leaflet.js. The application runs entirely in the browser with no backend services or build processes required.

## Working Effectively

- **NEVER CANCEL BUILDS OR COMMANDS** - All operations complete within seconds since this is a static application
- Serve the application:
  - `cd /home/runner/work/mapa_FCU/mapa_FCU`
  - `python3 -m http.server 8000` -- completes instantly, serves on http://localhost:8000
- **CRITICAL**: No build process exists - this is pure HTML/CSS/JavaScript
- **CRITICAL**: No package.json, npm, or node dependencies - everything is static files
- All JavaScript libraries are included as static files in the `js/` directory
- CSS frameworks are included as static files in the `css/` directory
- Map data is stored as JavaScript files in the `data/` directory

## Validation Scenarios

**ALWAYS manually validate changes by running complete user scenarios:**

1. **Basic Map Functionality**:
   - Load http://localhost:8000 in browser
   - Verify the map displays São Paulo municipalities (outlined regions)
   - Click on any municipality to see popup with information (id, name, description)
   - Verify popup displays correctly and can be closed

2. **Layer Controls**:
   - Click the "Layers" control in top-right corner
   - Toggle different layers on/off (municipalities, favelas setorizadas, favelas não setorizadas)
   - Verify layers show/hide correctly
   - Verify layer legends update appropriately

3. **Interactive Features**:
   - Test zoom in/out controls (+ and - buttons)
   - Test location control (target icon) - should attempt geolocation
   - Test measure tool - draw lines/polygons to measure distances/areas
   - Test search/geocoding functionality if available

4. **Data Integrity**:
   - Verify all favelas/communities data loads and displays
   - Check that popup information shows correctly for different data types
   - Ensure legends display proper imagery for each layer

## Repository Structure

```
/
├── index.html              # Main application page with embedded map
├── css/                    # Stylesheets directory
│   ├── leaflet.css        # Core Leaflet styles
│   ├── L.Control.*.css    # Plugin stylesheets
│   └── qgis2web.css       # Custom application styles
├── js/                     # JavaScript libraries directory
│   ├── leaflet.js         # Core Leaflet mapping library
│   ├── leaflet-*.js       # Leaflet plugins (measure, geocoder, etc.)
│   ├── labels.js          # Custom labeling functionality
│   └── qgis2web_expressions.js # Custom expressions
├── data/                   # Map data directory
│   └── *.js               # GeoJSON data as JavaScript files
└── legend/                 # Map legend images
    └── *.png              # Legend PNG files for each layer
```

## Key Technical Details

- **Technology**: HTML5, CSS3, JavaScript with Leaflet.js mapping library
- **Data Format**: GeoJSON data embedded in JavaScript files
- **No Dependencies**: All libraries included as static files, no package managers
- **No Build Process**: Direct file editing, refresh browser to see changes
- **Responsive Design**: Works on desktop and mobile devices
- **Performance**: Instant loading since all assets are local static files

## Common Development Tasks

- **Modifying Map Appearance**: Edit `css/qgis2web.css` for custom styling
- **Adding New Layers**: Add GeoJSON data to `data/` and reference in `index.html`
- **Updating Layer Data**: Edit existing JavaScript files in `data/` directory
- **Customizing Popups**: Modify popup HTML generation in `index.html`
- **Adding Map Controls**: Include new Leaflet plugins in `js/` and reference in HTML

## Testing and Validation

- **Local Testing**: `python3 -m http.server 8000` -- instant startup
- **Browser Compatibility**: Test in Chrome, Firefox, Safari, Edge
- **Mobile Testing**: Use browser dev tools mobile emulation
- **No Automated Tests**: Manual testing required for all changes
- **Performance**: Application loads instantly, no build time considerations

## Data Sources and Content

- **Municipality Data**: São Paulo state administrative boundaries
- **FCU Data**: Favelas e Comunidades Urbanas (favelas and urban communities)
  - Setorizadas: Communities included in census sectors
  - Não Setorizadas: Communities not included in census sectors
- **Data Source**: IBGE Censo 2022 (Brazilian Institute of Geography and Statistics)

## Important Limitations

- **Static Data**: No real-time updates, data must be manually updated
- **No Backend**: Cannot save user data or preferences
- **Browser Dependent**: Requires modern browser with JavaScript enabled
- **File Protocol**: Must be served via HTTP, cannot open as file:// due to CORS restrictions

**Remember**: This is a pure static web application. Any changes are immediately visible upon browser refresh. There are no build processes, dependency installations, or server deployments required.

Fixes #3.