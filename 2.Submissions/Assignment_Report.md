# SPATIAL INTELLIGENCE - APARTMENT COMPLEX ASSIGNMENT REPORT


###  Data Processing Steps

#### Step 1: Loading Geometry
```
- Load OBJ files using Topology.ByOBJPath()
- Convert to CellComplex structure for topological analysis
```

#### Step 2: Room Extraction and Tagging
- Extract individual rooms from the building geometry
- Assign semantic information via dictionaries:
  - **Room Names**: Living Room, Bedroom, Kitchen, Bathroom, etc.
  - **Color Coding**: Visual distinction for each room type

#### Step 3: Aperture Processing
- Extract door and window faces
- Tag with aperture type and color properties
- Calculate centroid positions for each aperture

#### Step 4: Spatial Relationship Analysis
- Create a graph representing spatial connectivity
- Use `Graph.ByTopology()` with parameters:
  - `viaSharedApertures=True`: Rooms connected through doors/windows
  - `toExteriorApertures=True`: Include connections to exterior

#### Step 5: Vertex and Edge Visualization
- Assign node sizes based on room surface area:
  - Larger nodes = Larger rooms
  - Smaller nodes = Smaller apertures
- Color code vertices by room/aperture type
- Encode edge properties (width and color)

---

## 4. COLOR MAPPING SCHEME

| Space Type | Color | Purpose |
|-----------|-------|---------|
| Living Room | Red | Main living area |
| Kitchen | Yellow | Food preparation |
| Dining Room | Pink | Dining area |
| Bedroom | Blue | Private sleeping areas |
| Bathroom | Purple | Sanitation facilities |
| Exterior Corridor | Grey | Outdoor circulation |
| Interior Corridor | Cyan | Indoor circulation |
| Door | Brown | Room connections |
| Window | Light Cyan | External connections |

---

## 5. GRAPH STRUCTURE ANALYSIS

### 5.1 Graph Vertices
- **Room Vertices**: Represent individual rooms, sized by surface area
- **Aperture Vertices**: Represent doors and windows
- **Total Vertices**: Comprises all rooms + doors + windows

### 5.2 Graph Edges
- Represent spatial adjacency relationships
- Connect rooms that share apertures (doors/windows)
- Enable pathfinding and spatial connectivity analysis

### 5.3 Connectivity Properties
- **Direct Connections**: Room-to-room via shared doors
- **Shared Apertures**: Multiple rooms connected through single aperture
- **Exterior Access**: Direct connections to exterior through windows/doors

---

## 6. VISUALIZATION OUTPUT

### 6.1 Spatial Representation Visualization
The generated visualization displays:
1. **Cell/Face Rendering**: 3D geometry of the apartment complex
   - Color-coded by room type
   - Proper face ordering and lighting

2. **Graph Overlay**: Network representation of spatial relationships
   - Node positions: Centroids of rooms/apertures
   - Node sizes: Proportional to surface area
   - Edge connections: Spatial adjacency relationships



---

## 7. KEY FINDINGS

### 7.1 Spatial Organization
- The building features a [number of rooms] room layout
- Clear separation of functional zones (bedrooms, common areas, service areas)
- Multiple circulation paths through corridors

### 7.2 Connectivity Insights
- Rooms are interconnected through [number] doors
- Windows provide [number] exterior connections
- Core circulation areas (corridors) act as distribution hubs

### 7.3 Graph Properties
- **Vertex Count**: [Total number of vertices]
- **Edge Count**: [Total number of edges]
- **Graph Density**: Indicates level of interconnectivity
- **Centrality**: Identifies key hub rooms (highest degree)

---

## 8. TOPOLOGICPY IMPLEMENTATION

### 8.1 Key Libraries Used
```python
from topologicpy.Topology import Topology
from topologicpy.Graph import Graph
from topologicpy.Cell import Cell
from topologicpy.Cluster import Cluster
from topologicpy.Dictionary import Dictionary
import math
```

### 8.2 Core Functions Applied
- `Topology.ByOBJPath()`: Import 3D geometry from OBJ files
- `Topology.SelfMerge()`: Merge connected geometric elements
- `Topology.Cells()`: Extract individual cells/rooms
- `Graph.ByTopology()`: Generate spatial relationship graph
- `Topology.Show()`: Visualize geometry and graph
- `Dictionary` operations: Attach semantic information to topologies

---

## 9. TECHNICAL CHALLENGES & SOLUTIONS

### Challenge 1: Room Identification
**Issue**: Extracting individual rooms from imported geometry
**Solution**: Use CellComplex structure with proper topology merging

### Challenge 2: Aperture Association
**Issue**: Linking doors/windows to their parent rooms
**Solution**: Process apertures separately and use centroid-based proximity matching

### Challenge 3: Visualization Clarity
**Issue**: Overlapping geometry in complex building
**Solution**: Use color coding, vertex sizing, and selective transparency

### Challenge 4: Graph Construction
**Issue**: Creating meaningful connectivity graph from 3D geometry
**Solution**: Leverage TopologicPy's built-in aperture-based connectivity analysis

---

## 10. LEARNING OUTCOMES

This assignment demonstrates understanding of:

1. **3D Geometric Modeling**: Working with complex 3D structures and topology
2. **Graph Theory Application**: Converting spatial geometry to graph networks
3. **Semantic Annotation**: Attaching meaning to geometric entities
4. **Data Visualization**: Multi-dimensional data representation
5. **TopologicPy Framework**: Advanced geometric computing capabilities

---

## 11. CONCLUSION

The spatial representation of the apartment complex successfully demonstrates the integration of geometric and topological analysis in Graph Machine Learning. The color-coded visualization with graph overlay provides intuitive understanding of:
- Spatial organization of the building
- Room connectivity and adjacency relationships
- Circulation patterns and accessibility
- Semantic differentiation of space types

This approach can be extended to:
- Navigation and pathfinding algorithms
- Space allocation and planning
- Energy efficiency analysis
- Emergency evacuation route planning
- Architectural design optimization

---

