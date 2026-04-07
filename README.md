# 🧱 OpenUSD Learning Checklist (Engineered Path)

## ✅ 1. Core Mental Model (Non-Negotiable)

Understand what OpenUSD actually *is*:

* [ ] USD is a **scene graph**, not a file format
* [ ] Everything = **Prims** (nodes in a hierarchy)
* [ ] Properties:

  * Attributes (data)
  * Relationships (links)
* [ ] Time is built-in (time-sampled data)

👉 If this doesn't click, everything else will feel confusing.

---

## 🌳 2. Scene Graph & Prims

* [ ] What is a **Stage**
* [ ] What is a **Prim**
* [ ] Prim hierarchy (parent/child)
* [ ] Paths (`/World/Atmosphere/CloudLayer`)
* [ ] Types:

  * `Xform`
  * `Mesh`
  * `Scope`
  * Custom schemas

👉 Think: this is your "Earth object model"

---

## 📦 3. Layers & Composition (THIS IS THE HARD PART)

This is where USD becomes powerful—and confusing.

* [ ] What is a **Layer (.usd, .usda, .usdc)**
* [ ] Layer stacking
* [ ] Composition arcs:

  * [ ] References
  * [ ] SubLayers
  * [ ] Payloads
  * [ ] Inherits
  * [ ] Variants

👉 Key idea:

> Your "Earth" is not one file—it's a **composition of many data sources**

---

## ⏱️ 4. Time & Animation (Critical for EO DT)

* [ ] TimeCodes
* [ ] Time-sampled attributes
* [ ] Interpolation
* [ ] Playback vs simulation time

👉 This is how you represent:

* Forecast timesteps
* Satellite passes
* Temporal evolution

---

## 🎨 5. Geometry & Transforms

* [ ] Mesh basics (points, faces)
* [ ] Normals, UVs
* [ ] `Xform` and transforms:

  * Translate / Rotate / Scale
* [ ] Instancing

👉 For Earth-2:

* Terrain tiles
* Atmospheric volumes
* Sensor frustums

---

## 🌐 6. Data Modeling for Scientific Data

This is where *you* go beyond most USD users.

* [ ] Storing scalar fields (temp, pressure)
* [ ] Encoding grids:

  * Structured vs unstructured
* [ ] Metadata on prims
* [ ] Units + coordinate systems

👉 You'll likely design schemas like:

```
/World/Atmosphere/Temperature_850mb
```

---

## 🔌 7. USD APIs (Python First)

* [ ] `pxr.Usd` basics
* [ ] Create a Stage
* [ ] Define a Prim
* [ ] Set attributes
* [ ] Read/write layers

Example mental model:

```python
stage = Usd.Stage.CreateNew("earth.usda")
prim = stage.DefinePrim("/World/Atmosphere", "Xform")
```

👉 This is your bridge from:

* NetCDF / GRIB2 → USD

---

## 🧬 8. Schemas (Where Things Get Real)

* [ ] Built-in schemas (UsdGeom, UsdShade, etc.)
* [ ] API schemas vs Typed schemas
* [ ] Creating custom schemas

👉 For EO DT:
You may define:

* Atmosphere schema
* Grid schema
* Forecast schema

---

## 🎛️ 9. Variants (Underrated Superpower)

* [ ] Variant sets
* [ ] Switching states

Example:

* Model A vs Model B
* Different forecast runs
* Different physics configs

---

## 🚀 10. Performance Concepts

* [ ] Payloads (lazy loading)
* [ ] Instancing
* [ ] Binary vs ASCII USD
* [ ] Scene complexity management

👉 Critical when your "scene" = the entire Earth

---

## 🔄 11. Interoperability

* [ ] USD ↔ Omniverse
* [ ] USD ↔ Blender / Unreal
* [ ] Converting:

  * NetCDF → USD
  * GeoTIFF → USD

---

## 🧠 12. EO DT-Specific Patterns (Advanced)

This is where you differentiate yourself:

* [ ] Representing gridded weather data in USD
* [ ] Streaming updates into a live Stage
* [ ] Layer-per-timestep vs time-sampled approach
* [ ] Hybrid:

  * Static terrain layer
  * Dynamic atmosphere layer

---

# 🔥 Suggested Learning Order (Don't Skip Around)

1. Core mental model
2. Prims + Stage
3. Layers & composition
4. Python API
5. Time
6. Geometry
7. Then everything else

---

# ⚠️ Common Pitfalls

* Treating USD like a file format ❌
* Ignoring composition arcs ❌
* Overloading a single layer ❌
* Not thinking in hierarchy ❌

---

# 🧭 What "Proficiency" Looks Like

You know you're solid when you can:

* Build a USD stage from scratch
* Merge multiple data sources via layers
* Stream time-varying data into a scene
* Design a schema for weather data
* Plug it into NVIDIA Omniverse without guessing
