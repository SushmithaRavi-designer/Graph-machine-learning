# SPATIAL INTELLIGENCE - APARTMENT COMPLEX ASSIGNMENT REPORT


## Data Processing Steps

#### Step 1: Import Required Libraries
- Import TopologicPy modules:
  - **Geometry**: Vertex, Edge, Wire, Face, Shell, Cell, CellComplex, Cluster, Topology
  - **Analysis**: Dictionary, Helper, Grid, Graph
  - **Visualization**: Color

#### Step 2: Check TopologicPy Version
- Verify installed version is 0.9.18 or newer
- Display current version using `Helper.Version()`

#### Step 3: Set Renderer Configuration
- Configure visualization backend:
  - **VSCode**: For VS Code integrated viewer
  - **Colab**: For Google Colab environments
  - **Browser**: For web-based visualization

#### Step 4: Import Main House OBJ File
- Load main building geometry using `Topology.ByOBJPath()`
- Input: complex house.obj file
- Output: List of topological objects representing the building structure

#### Step 5: Convert List to Cluster
- Convert OBJ list to `Cluster` using `Cluster.ByTopologies()`
- Create `CellComplex` from cluster using `CellComplex.ByFacesCluster()`
- Result: Unified topological structure for further analysis

#### Step 6: Import Doors and Windows OBJ Files
- Load aperture geometries:
  - **Doors**: complex_door.obj
  - **Windows**: complex_window.obj
- Extract faces using `Topology.Faces()` on converted clusters
- Count and catalog all apertures in the structure

#### Step 7: Cell Extraction and Color Tagging
- Extract individual cells/rooms from house geometry
- Define color map for semantic categorization:
  - **Living Room**: Red
  - **Kitchen**: Yellow
  - **Dining Room**: Pink
  - **Bedroom**: Blue
  - **Bathroom**: Purple
  - **Corridors**: Cyan (interior), Grey (exterior)
  - **Doors**: Brown
  - **Windows**: Light Cyan
- Tag each cell with name and color using `Dictionary`
- Create selector vertices for each room (internal vertices)

#### Step 8: Creating CellComplex with Apertures
- Add doors to cell complex using `Topology.AddApertures()` with `subTopologyType="face"`
- Add windows to cell complex using `Topology.AddApertures()` with `subTopologyType="face"`
- Create updated CellComplex with aperture relationships

#### Step 9: Aperture Data Extraction & Connectivity Graph Creation
- Create spatial graph using `Graph.ByTopology()` with parameters:
  - `direct=False`: Allow indirect connections
  - `viaSharedApertures=True`: Connect rooms sharing doors/windows
  - `toExteriorApertures=True`: Include exterior connections
- Assign vertex properties:
  - **Size**: Normalized based on room surface area (8-28 units)
  - **Color**: Derived from cell color dictionary
- Assign edge properties:
  - **Width**: Set to 10 units
  - **Color**: Set to black for visual distinction
- Create aperture vertices for doors and windows at their centroids

#### Step 10: Visualization
- Display final graph with room cells and apertures
- Use `Topology.Show()` with:
  - `vertexSizeKey="size"`: Vertex size proportional to room area
  - `vertexColorKey="color"`: Color-coded by room/aperture type
  - `backgroundColor="white"`: White background for clarity
  - Specified renderer configuration

---

## 2. COLOR MAPPING SCHEME

| Space Type | Hex Color | Purpose |
|-----------|-----------|---------|
| Living Room | #FF0000 (Red) | Main living area |
| Kitchen | #FFFF00 (Yellow) | Food preparation |
| Dining Room | #FF1493 (Pink) | Dining area |
| Bedroom | #0000FF (Blue) | Private sleeping areas |
| Bathroom | #800080 (Purple) | Sanitation facilities |
| Exterior Corridor | #808080 (Grey) | Outdoor circulation |
| Interior Corridor | #00FFFF (Cyan) | Indoor circulation |
| Door | #8B4513 (Brown) | Room connections |
| Window | #E0FFFF (Light Cyan) | External connections |

---

## 3. GRAPH STRUCTURE ANALYSIS

### 3.1 Graph Vertices
- **Room Vertices**: Represent individual rooms/cells extracted from CellComplex
  - Sized proportionally to their surface area
  - Normalized size range: 8-28 units for visual distinction
- **Aperture Vertices**: Represent doors and windows
  - Doors: Size 5, Brown color
  - Windows: Size 4, Light Cyan color
  - Positioned at face centroids
- **Total Vertices**: Comprises all extracted cells (rooms) plus aperture vertices

### 3.2 Graph Edges
- Represent spatial adjacency relationships created by `Graph.ByTopology()`
- Edge properties:
  - **Width**: 10 units for visibility
  - **Color**: Black for standard contrast
- Connection logic:
  - Rooms connected via shared doors/windows (`viaSharedApertures=True`)
  - Exterior connections included (`toExteriorApertures=True`)
  - Indirect connections allowed (`direct=False`)

### 3.3 Connectivity Properties
- **Via Shared Apertures**: Rooms are connected when they share door/window faces
- **Exterior Access**: Direct connections to outside environment through external apertures
- **Network Topology**: Creates a spatial graph enabling pathfinding and analysis

---

## 4. VISUALIZATION OUTPUT

### 4.1 3D Spatial Representation
The generated visualization displays:
1. **Building Geometry**: 3D model of the apartment complex
   - Color-coded cells representing different room types
   - Door and window faces included for aperture visualization
   - White background for clarity

2. **Graph Overlay**: Network representation of spatial relationships
   - Node positions: Centroids of rooms and apertures
   - Node sizes: Proportional to room surface area (rooms larger than apertures)
   - Edge connections: Black lines showing spatial adjacency
   - Color coding: Semantic differentiation by room/aperture type

---

## 5. KEY FINDINGS & METRICS

### 5.1 Spatial Organization
- Building comprises multiple room types organized by function
- Clear separation of functional zones (bedrooms, common areas, service areas)
- Multiple circulation paths through interior and exterior corridors
- Color-coded organization enables intuitive spatial understanding

### 5.2 Graph Metrics
Derived from `Graph.ByTopology()` analysis:
- **Vertex Count**: Number of rooms + apertures in the network
- **Edge Count**: Number of spatial adjacency relationships
- **Graph Connectivity**: Indicates how well-connected the building spaces are
- **Centrality**: Identifies key hub rooms with highest connectivity degree

### 5.3 Aperture Analysis
- **Door Count**: Number of room-to-room connections
- **Window Count**: Number of exterior connections
- **Connection Patterns**: Reveals primary circulation routes and dead-end spaces

---

## 6. TECHNICAL IMPLEMENTATION

### 6.1 TopologicPy Workflow
```
OBJ Files → Load → Cluster → CellComplex → Aperture Processing → 
Graph Creation → Vertex/Edge Properties → Visualization
```

### 6.2 Key Functions Applied
- `Topology.ByOBJPath()`: Import 3D geometry from OBJ files
- `Cluster.ByTopologies()`: Aggregate topologies into unified cluster
- `CellComplex.ByFacesCluster()`: Create structured cell complex
- `Topology.AddApertures()`: Integrate doors/windows into cell complex
- `Graph.ByTopology()`: Generate connectivity graph with adjacency relationships
- `Dictionary` operations: Attach semantic properties (name, color, size)
- `Topology.Show()`: Render 3D visualization with graph overlay

### 6.3 Color Normalization
- Surface area extracted using `Cell.SurfaceArea()`
- Normalized range: 0 to 1 based on min/max areas
- Applied to vertex sizing with formula: `size = 8 + 20 * (norm^0.5)`
- Result: Visual distinction between large rooms and small apertures

---

## 7. TECHNICAL CHALLENGES & SOLUTIONS

### Challenge 1: Room Identification
**Issue**: Extracting individual rooms from imported geometry
**Solution**: Use CellComplex structure with proper topology merging and `Topology.SelfMerge()` to create unified cell representation from imported OBJ faces

### Challenge 2: Aperture Association
**Issue**: Linking doors/windows to their parent rooms for connectivity analysis
**Solution**: Process apertures separately using dedicated OBJ files, then integrate via `Topology.AddApertures()` to establish spatial relationships

### Challenge 3: Vertex Sizing and Normalization
**Issue**: Creating meaningful visual distinction between rooms and apertures
**Solution**: Extract surface area using `Cell.SurfaceArea()`, normalize to 0-1 range, and apply square root scaling with formula: `size = 8 + 20 * (norm^0.5)` for improved visual spread

### Challenge 4: Color Consistency and Mapping
**Issue**: Ensuring consistent color representation across geometry and graph visualization
**Solution**: Use hex color values in Dictionary format (e.g., "#FF0000" for red) and map room names to colors during extraction phase

### Challenge 5: Graph Construction from Complex Geometry
**Issue**: Creating meaningful connectivity graph from 3D spatial data
**Solution**: Leverage TopologicPy's `Graph.ByTopology()` with strategic parameters:
  - `viaSharedApertures=True`: Connect only rooms that share aperture faces
  - `toExteriorApertures=True`: Include exterior environment connections
  - `direct=False`: Allow indirect adjacency relationships

### Challenge 6: Visualization Clarity in Complex Space
**Issue**: Overlapping geometry and visual clutter in 3D building visualization
**Solution**: 
  - Use white background for contrast
  - Color-code vertices by room/aperture type
  - Scale vertex sizes proportionally for visual hierarchy
  - Apply black edges with controlled width for clear connectivity representation

---