# Building Data Share (BDS) File Format

**Building Data Share (BDS)** is an open-source, XML-based schema for defining reusable data schedules in building projects. It enables project teams to create standardized templates for extracting information from BIM models, ensuring everyone uses the same definitions for schedules and reports.

BDS is built on the IFC (Industry Foundation Classes) standard — an open, global schema for building industry data — so it works with any IFC-compliant model. In practice, an AEC team (architects, engineers, contractors, etc.) can use BDS to set up internal schedule templates: specifying which IFC classes (like walls, doors, or spaces) and which attributes or property values to include. These templates can then be shared across projects and teams, helping maintain consistency and improve collaboration.

* **Interdisciplinary use:** Covers all AEC disciplines by leveraging IFC model classes (e.g., *IfcWall*, *IfcDoor*, *IfcSpace*). Any software that reads IFC can use BDS templates to extract data.
* **Template sharing:** Define schedules once and reuse them. A BDS file can be distributed so everyone uses the same field and filter definitions, ensuring smoother multi-project coordination.
* **Standardized outputs:** Produces consistent, structured tables of model data. Every column and row is pre-defined, making exported schedules uniform and easier to compare or aggregate.

The schema file is available at: [`g-algos/standards/bds.1.0.xsd`](https://github.com/g-algos/standards/bds.1.0.xsd)

---

