# Request 18 (validated)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Finish S3 before the rival can flood the fords: deliver S3 first, then simulate until the episode ends and report delivered and stolen parcels.

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "stop_order": ["S3"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 128.0, "steps": 71, "delivery_order": [{"stop": "S3", "step": 24}, {"stop": "S1", "step": 37}, {"stop": "S4", "step": 54}, {"stop": "S2", "step": 71}], "terrain_steps": {"road": 36, "grass": 18, "mud": 14, "ford": 3}, "ford_steps": [24, 31, 65], "stops": ["S1", "S2", "S3", "S4"], "avoid_terrain": [], "nodes_expanded": 1741, "uses_tunnel": true}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": [24, 31, 65]}`

**Thought (Reason):** The plan delivers S3 first, at step 24, for a total cost of 128. The rival has not used its dam yet, so I'll run the simulation to the end of the episode.

**Action (Act):** `simulate({"steps": 200})`

**Observation (Sense):** `{"t": 99, "position": [0, 1], "rival": [3, 6], "cost_so_far": 155.0, "delivered": ["S1", "S2", "S4"], "stolen": ["S3"], "dam_used": true, "flood_steps_left": 0, "finished": true, "events": ["t=6: slip: S -> W, now at (10, 10)", "t=22: slip: S -> E, now at (20, 11)", "t=23: slip: S -> W, now at (20, 10)", "t=30: slip: S -> E, now at (19, 14)", "t=35: slip: E -> S, now at (22, 13)", "t=38: rival stole parcel at (22, 17)", "t=41: rival opened the dam", "t=43: slip: E -> S, now at (22, 12)", "t=61: slip: W -> S, now at (22, 7)", "t=64: delivered at (21, 5)", "t=75: slip: W -> N, now at (12, 5)", "`

**Thought (Reason):** The S3-first plan failed: the rival stole the S3 parcel before I could deliver it.

**Outcome (episode finished at t=99):**
- **Delivered:** S1 (t=64), S4 (t=81), S2 (t=98)
- **Stolen:** S3. The rival reached (22, 17) at t=38, before my robot did. The robot was slipping off course at that point, so it arrived late.
- **Dam:** the rival opened it at t=41, but the flood had already expired by the end of the run.
- **Cost:** 155 so far, against the planned 128. The extra cost comes from repeated slips.

The S3 delivery was not completed, so the request was not fully met. Since S3 is itself a ford and sits near the rival's path, a route that reaches it earlier, or a plan that accounts for the rival's approach, would be needed to protect that parcel.

**Final answer:**

The S3-first plan failed: the rival stole the S3 parcel before I could deliver it.

**Outcome (episode finished at t=99):**
- **Delivered:** S1 (t=64), S4 (t=81), S2 (t=98)
- **Stolen:** S3. The rival reached (22, 17) at t=38, before my robot did. The robot was slipping off course at that point, so it arrived late.
- **Dam:** the rival opened it at t=41, but the flood had already expired by the end of the run.
- **Cost:** 155 so far, against the planned 128. The extra cost comes from repeated slips.

The S3 delivery was not completed, so the request was not fully met. Since S3 is itself a ford and sits near the rival's path, a route that reaches it earlier, or a plan that accounts for the rival's approach, would be needed to protect that parcel.