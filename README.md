# Agentic Map

An AI-powered interface for the Van Buren County Parcel Viewer, using ChatBase for natural language interactions with the map.

## Project Overview

This project creates a simple interface that allows users to interact with the Van Buren County Mango Maps Parcel Viewer using natural language through a ChatBase AI chatbot.

### Current Implementation

The project uses URL parameters to control the map view:
```
https://gis.vanburencountymi.gov/van-buren-county-mi/maps/139519/parcel-viewer?field=parcel_no&value=[PARCEL_NUMBER]&layer=b386acf6-77e2-11ee-be3d-027d7e0bb32b&preview=true
```

## Project Structure

- `index.html`: Main application file containing:
  - Mango Maps iframe
  - ChatBase chat interface
  - JavaScript for map control
  - Tool registration for ChatBase to enable map updates

- `test-postmessage.html`: Test file created to explore iframe communication possibilities
  - Attempts to use postMessage API to communicate directly with the map interface
  - Currently unsuccessful due to same-origin policy restrictions

## Technical Implementation Details

### Current Working Method
- Uses URL parameters to update the map view
- Requires full iframe reload for each update
- ChatBase custom action called `updateMapView` updates the iframe src
- Known limitation: Reload is slow and requires re-accepting terms

### Attempted Optimizations
We attempted to improve the user experience by:
1. **Direct DOM Manipulation**: Not possible due to cross-origin restrictions in iframes
2. **PostMessage Communication**: Tested but received no responses from the Mango Maps application
3. **API Integration**: No public API available from Mango Maps

## Usage

The AI can control the map view by calling the `updateMapView(fieldName, fieldValue)` function, which updates the iframe's URL with the appropriate parameters. 

Example parameters:
- fieldName: 'parcel_no'
- fieldValue: '80-14-021-006-00'

## Setup Instructions

1. Add your ChatBase integration code to the designated section in `index.html`
2. Serve the files using any basic web server
3. Access the page and interact with the AI to control the map

## Known Limitations

1. Each map update requires a full iframe reload
2. Users must re-accept terms after each reload
3. No direct interaction with map interface possible due to iframe restrictions
4. Slow load times due to full page reloads

## Future Improvements

Potential areas for improvement if Mango Maps adds features:
1. API access for direct map control
2. PostMessage support for iframe communication
3. Option to disable terms acceptance requirement
4. Parameters for controlling UI elements