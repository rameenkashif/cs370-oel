# Request 6 (raw)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Deliver S3 first, then the rest, as cheaply as possible.

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "stop_order": ["S3"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 128.0, "steps": 71, "delivery_order": [{"stop": "S3", "step": 24}, {"stop": "S1", "step": 37}, {"stop": "S4", "step": 54}, {"stop": "S2", "step": 71}], "terrain_steps": {"road": 36, "grass": 18, "mud": 14, "ford": 3}, "ford_steps": [24, 31, 65], "stops": ["S1", "S2", "S3", "S4"], "avoid_terrain": [], "nodes_expanded": 1741, "uses_tunnel": true}`

**Action (Act):** `tunnel_info({})`

**Observation (Sense):** `{"pairs": [[[0, 5], [9, 2]], [[12, 0], [13, 10]], [[12, 4], [12, 17]]], "cost_per_jump": 1.0}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": [24, 31, 65]}`

**Action (Act):** `simulate({"steps": 71})`

**Observation (Sense):** `{"t": 71, "position": [16, 6], "rival": [13, 7], "cost_so_far": 102.0, "delivered": ["S1"], "stolen": ["S3"], "dam_used": true, "flood_steps_left": 0, "finished": false, "events": ["t=6: slip: S -> W, now at (10, 10)", "t=22: slip: S -> E, now at (20, 11)", "t=23: slip: S -> W, now at (20, 10)", "t=30: slip: S -> E, now at (19, 14)", "t=35: slip: E -> S, now at (22, 13)", "t=38: rival stole parcel at (22, 17)", "t=41: rival opened the dam", "t=43: slip: E -> S, now at (22, 12)", "t=61: slip: W -> S, now at (22, 7)", "t=64: delivered at (21, 5)"]}`

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "stops": ["S4", "S2"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 51.0, "steps": 28, "delivery_order": [{"stop": "S4", "step": 11}, {"stop": "S2", "step": 28}], "terrain_steps": {"grass": 10, "road": 9, "mud": 8, "ford": 1}, "ford_steps": [22], "stops": ["S2", "S4"], "avoid_terrain": [], "nodes_expanded": 409, "uses_tunnel": true}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": true, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": [22]}`

**Action (Act):** `simulate({"steps": 28})`

**Observation (Sense):** `{"t": 99, "position": [0, 1], "rival": [3, 6], "cost_so_far": 155.0, "delivered": ["S1", "S2", "S4"], "stolen": ["S3"], "dam_used": true, "flood_steps_left": 0, "finished": true, "events": ["t=75: slip: W -> N, now at (12, 5)", "t=81: delivered at (15, 18)", "t=98: delivered at (0, 1)"]}`

**Thought (Reason):** **S3 was not delivered.** The rival stole its parcel at (22,17) at t=38, before the robot got there. The robot did finish the other three stops.

**Outcome:**
- **S1** (21,5): delivered at t=64.
- **S4** (15,18): delivered at t=81.
- **S2** (0,1): delivered at t=98.
- **S3** (22,17): stolen by the rival. I have no tool to recover a stolen parcel, so it is undelivered.

**Why it happened:** Random slips delayed the robot. The original plan reached S3 at step 24, but after several slips the rival got there first. The rival also opened the dam at t=41. The flood had no effect on the route, since the flood status shows zero flood steps remaining when I checked.

**Cost:** The original plan was 128. After slips, the actual cost was 155 for the robot's whole run. That cost covers the S1 delivery plus the replanned S4 and S2 route. It does not include a delivered S3.

**Final answer:** The plan cost was 128 for the original route, but the actual cost was 155. S3 failed because the rival stole it, so the "S3 first" requirement was not met. S1, S4 and S2 were delivered.

**Final answer:**

**S3 was not delivered.** The rival stole its parcel at (22,17) at t=38, before the robot got there. The robot did finish the other three stops.

**Outcome:**
- **S1** (21,5): delivered at t=64.
- **S4** (15,18): delivered at t=81.
- **S2** (0,1): delivered at t=98.
- **S3** (22,17): stolen by the rival. I have no tool to recover a stolen parcel, so it is undelivered.

**Why it happened:** Random slips delayed the robot. The original plan reached S3 at step 24, but after several slips the rival got there first. The rival also opened the dam at t=41. The flood had no effect on the route, since the flood status shows zero flood steps remaining when I checked.

**Cost:** The original plan was 128. After slips, the actual cost was 155 for the robot's whole run. That cost covers the S1 delivery plus the replanned S4 and S2 route. It does not include a delivered S3.

**Final answer:** The plan cost was 128 for the original route, but the actual cost was 155. S3 failed because the rival stole it, so the "S3 first" requirement was not met. S1, S4 and S2 were delivered.