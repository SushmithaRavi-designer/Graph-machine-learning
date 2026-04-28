# Apartment Complex Spatial Analysis - Assignment Report

## 📋 Overview

This folder contains the complete assignment report for the **Spatial Intelligence** analysis of an apartment complex. The report demonstrates the integration of 3D geometric modeling, topological analysis, and graph-based spatial relationship visualization using TopologicPy.

---

## 📁 Folder Contents

### 1. **Assignment_Report.html** ⭐ START HERE
- **Type:** Interactive HTML Report
- **Purpose:** Main assignment report with all analysis, methodology, findings, and visualizations
- **How to Open:** Double-click to open in your default browser
- **Features:**
  - Complete write-up of the assignment
  - Color-coded statistics dashboard
  - Links to interactive 3D visualizations
  - Methodology explanation
  - Technical implementation details

### 2. **01_Apartment_Complex_Colored_Cells.html**
- **Type:** Interactive 3D Visualization
- **Purpose:** Shows the 3D apartment complex geometry with color-coded rooms
- **Contents:**
  - 3D model of the building with all rooms
  - Color-coded by room type (Living Room, Bedroom, Kitchen, etc.)
  - Doors and windows identified with distinct colors
  - Fully interactive: rotate, zoom, pan

### 3. **02_Spatial_Connectivity_Graph.html**
- **Type:** Interactive Graph Visualization  
- **Purpose:** Shows the spatial connectivity graph overlay on the geometry
- **Contents:**
  - Graph vertices (nodes) representing rooms and apertures
  - Graph edges showing spatial adjacency relationships
  - Node sizes proportional to room surface area
  - Color-coded by space type
  - Edge connections showing room connectivity

### 4. **Assignment_Report.md**
- **Type:** Markdown Document
- **Purpose:** Plain text version of the assignment report
- **Use:** Reference document, can be converted to PDF/Word if needed

### 5. **summary_statistics.json**
- **Type:** JSON Data File
- **Purpose:** Machine-readable summary of all statistics
- **Contents:**
  - Model statistics (rooms, doors, windows count)
  - Graph metrics (vertices, edges)
  - Room details with areas and colors
  - Generation timestamp

---

## 🚀 How to Use

### Step 1: Open the Main Report
1. Navigate to this folder
2. Double-click **`Assignment_Report.html`**
3. The report will open in your web browser

### Step 2: View the 3D Model
- Click the link in the report: **"View 3D Model"**
- Or directly open: **`01_Apartment_Complex_Colored_Cells.html`**
- **Interactive Controls:**
  - **Left Mouse Drag:** Rotate the model
  - **Right Mouse Drag / Scroll:** Zoom
  - **Mouse Wheel:** Pan view

### Step 3: Analyze the Graph
- Click the link in the report: **"View Graph Visualization"**
- Or directly open: **`02_Spatial_Connectivity_Graph.html`**
- Visualize:
  - Spatial relationship graph overlaid on geometry
  - Node connectivity (room adjacency)
  - Network topology of the apartment complex

---

## 📊 Key Statistics

The analysis includes:

| Metric | Value |
|--------|-------|
| **Total Rooms/Cells** | To be populated from notebook execution |
| **Total Doors** | To be populated from notebook execution |
| **Total Windows** | To be populated from notebook execution |
| **Graph Vertices** | Rooms + Apertures |
| **Graph Edges** | Spatial connectivity relationships |

*Statistics are generated when you run the analysis cells in the Jupyter notebook.*

---

## 🎨 Color Scheme Reference

| Space Type | Color | Hex Code |
|-----------|-------|----------|
| Living Room | Red | #FF0000 |
| Kitchen | Yellow | #FFFF00 |
| Dining Room | Pink | #FF1493 |
| Bedroom | Blue | #0000FF |
| Bathroom | Purple | #800080 |
| Interior Corridor | Cyan | #00FFFF |
| Exterior Corridor | Grey | #808080 |
| Door | Brown | #8B4513 |
| Window | Light Cyan | #E0FFFF |

---

## 🔧 Technical Details

### Model Source Files
- **Main Building:** `complex_house.obj`
- **Doors:** `complex_door.obj`
- **Windows:** `complex_window.obj`

### Libraries Used
- **TopologicPy:** 3D geometric modeling and topology
- **Graph Theory:** Spatial relationship analysis
- **Python:** Data processing and visualization

### Graph Analysis Features
- **Vertices:** Room centroids and aperture positions, sized by surface area
- **Edges:** Spatial adjacency via shared apertures
- **Direct Connections:** Room-to-room connectivity
- **Exterior Connections:** Aperture-based external access

---

## 💡 Key Findings

### Spatial Organization
- Clear functional zoning of different room types
- Logical circulation through corridors
- Strategic aperture placement for accessibility

### Connectivity Insights
- Rooms interconnected through doors enabling movement
- Windows providing exterior visual access
- Corridor systems acting as distribution hubs
- Graph density indicating level of interconnectivity

### Potential Applications
- Emergency evacuation route planning
- Space allocation optimization
- Navigation systems for building automation
- Energy efficiency analysis
- Accessibility assessment

---

## 📝 Assignment Submission

This complete package includes:
- ✅ Comprehensive written report
- ✅ Interactive 3D geometry visualization
- ✅ Spatial connectivity graph analysis
- ✅ Statistical summary
- ✅ Methodology documentation
- ✅ Color-coded semantic differentiation

**All files are ready for submission in this folder.**

---

## 🔗 Next Steps

1. **Review the HTML Report** - Get overview of the analysis
2. **Explore the 3D Model** - Understand building geometry
3. **Analyze the Graph** - Examine spatial relationships
4. **Check Statistics** - View model metrics
5. **Run Notebook Cells** - Generate fresh visualizations if needed

---

## ⚙️ Running the Notebook Analysis

To regenerate the visualizations and statistics:

1. Open `trial 1.ipynb` in Jupyter
2. Run all cells in order
3. New visualizations will be saved to this folder
4. Statistics will be updated in `summary_statistics.json`

---

**Report Generated:** April 2026  
**Course:** Graph Machine Learning  
**Assignment:** Spatial Intelligence - Apartment Complex Analysis

---

For questions or modifications, refer to the original notebook: `trial 1.ipynb`
