# Request 14 (raw)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Avoid fords completely and deliver all four parcels.

**Action (Act):** `plan_route({"algorithm": "astar", "avoid_terrain": ["ford"], "heuristic": "tunnel_mst", "stops": ["S1", "S2", "S3", "S4"]})`

**Observation (Sense):** `{"ok": false, "error": "no route found (search failed)", "expanded": 3028}`

**Action (Act):** `plan_route({"algorithm": "ucs", "avoid_terrain": ["ford"], "heuristic": "zero", "stops": ["S1", "S2", "S3", "S4"]})`

**Observation (Sense):** `{"ok": false, "error": "no route found (search failed)", "expanded": 3028}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": null}`

**Action (Act):** `plan_route({"algorithm": "ucs", "avoid_terrain": ["ford"], "heuristic": "zero", "stops": ["S1", "S4"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "ucs", "heuristic": "zero", "cost": 53.0, "steps": 29, "delivery_order": [{"stop": "S4", "step": 12}, {"stop": "S1", "step": 29}], "terrain_steps": {"road": 11, "grass": 9, "mud": 9}, "ford_steps": [], "stops": ["S1", "S4"], "avoid_terrain": ["ford"], "nodes_expanded": 860, "uses_tunnel": true}`

**Thought (Reason):** I can't deliver all four parcels without using a ford, so I haven't run a delivery.

- **S3 (22, 17) is itself a ford.** Any delivery there requires entering a ford.
- **S2 (0, 1) can only be reached through fords.** Searches that avoid fords fail, with and without the heuristic (A* with tunnel_mst, and UCS). The search expanded about 3,000 nodes each time and found no route.

A partial route is feasible. Delivering only S4 and S1, avoiding fords and using a teleport tunnel, costs 53 with 29 steps:
- S4 at step 12
- S1 at step 29

Terrain used is 11 road, 9 grass and 9 mud, with no ford steps. I haven't executed it. Should I run this two-stop plan, or do you want something else, such as allowing fords for S2 and S3?

**Final answer:**

I can't deliver all four parcels without using a ford, so I haven't run a delivery.

- **S3 (22, 17) is itself a ford.** Any delivery there requires entering a ford.
- **S2 (0, 1) can only be reached through fords.** Searches that avoid fords fail, with and without the heuristic (A* with tunnel_mst, and UCS). The search expanded about 3,000 nodes each time and found no route.

A partial route is feasible. Delivering only S4 and S1, avoiding fords and using a teleport tunnel, costs 53 with 29 steps:
- S4 at step 12
- S1 at step 29

Terrain used is 11 road, 9 grass and 9 mud, with no ford steps. I haven't executed it. Should I run this two-stop plan, or do you want something else, such as allowing fords for S2 and S3?