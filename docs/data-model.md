# OpenClimb Data Model

## Purpose

This document defines the core data model used throughout OpenClimb.

It describes the relationships between all major objects in the application.

---

# Hierarchy

Country
↓
Area
↓
Crag
↓
Sector
↓
Route

---

# Country

Represents a country.

Properties:

- name
- code

Example:

Poland

---

# Area

A geographical climbing area.

Example:

Karkonosze

Properties:

- name
- description
- countries

Contains:

- Crags

---

# Crag

A climbing crag or climbing location.

Example:

Złoty Las

Properties:

- name
- rock type
- description
- approach time
- parking
- child friendly
- maximum height
- difficulty range
- exposition
- sport routes
- trad routes
- photos

Contains:

- Sectors

---

# Sector

A section of a crag.

Example:

Sector A

Properties:

- name
- description
- exposition
- maximum height
- photo
- topo
- number of routes

Contains:

- Routes

---

# Route

A climbing route.

Properties:

- name
- author grade
- community grade
- climbing type
- bolts
- route height
- protection character
- route character
- author
- year
- description
- history
- warnings
- photos
- topo
- user rating
- classic

---

# User

Properties:

- nickname
- avatar
- joined
- climbed routes
- climbed classics
- favourite routes
- ratings

---

# Parking

Properties:

- name
- coordinates

---

# Photos

Photos may belong to:

- Crag
- Sector
- Route

---

# Topo

Topo belongs only to:

- Sector
- Route

---

# Relationships

Country

└── Area

    └── Crag

        ├── Parking

        ├── Photos

        └── Sector

              ├── Photo

              ├── Topo

              └── Route

                    ├── Photos

                    └── User Ratings

---

# Design Principles

- Every Route belongs to exactly one Sector.
- Every Sector belongs to exactly one Crag.
- Every Crag belongs to exactly one Area.
- Every Area belongs to at least one Country.
- Photos can be shared across the application.
- Community data never replaces the author's original data.
- ## Core Rules

- Author grade is immutable.
- Community grade is calculated independently.
- Both grades are always displayed.
