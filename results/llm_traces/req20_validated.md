# Request 20 (validated)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Use weighted A* to deliver S1, S2 and S4 without fords, then check the flood status of that plan.

**Action (Act):** `plan_route({"algorithm": "wastar", "avoid_terrain": ["ford"], "heuristic": "tunnel_mst", "stops": ["S1", "S2", "S4"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "wastar", "heuristic": "tunnel_mst", "cost": 90.0, "steps": 58, "delivery_order": [{"stop": "S1", "step": 19}, {"stop": "S4", "step": 36}, {"stop": "S2", "step": 58}], "terrain_steps": {"road": 32, "grass": 17, "mud": 9}, "ford_steps": [], "stops": ["S1", "S2", "S4"], "avoid_terrain": ["ford"], "nodes_expanded": 364, "uses_tunnel": true}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": []}`

**Thought (Reason):** The weighted A* plan delivers S1, S2 and S4 without touching any ford, with a total cost of **90**.

**Plan (weighted A*, tunnel_mst heuristic, fords avoided):**
- S1 delivered at step 19
- S4 delivered at step 36
- S2 delivered at step 58
- 58 steps in total: 32 road, 17 grass, 9 mud, and the route uses a teleport tunnel.
- The search expanded 364 nodes.

**Flood status:**
- The rival has not used its dam charge, so no flooding is active (0 flood steps left).
- The current plan has no ford steps, so it is not exposed to a flood.
- The status lists S2 among stops that "need a ford." The plan still reaches S2 without crossing a ford, so that label does not affect this route. It would matter if the route were replanned to allow fords.
- S3 is itself a ford cell. It is not part of this request, so I did not plan for it.

I did not run the simulation, since you only asked for the plan and its flood check.

**Final answer:** The plan delivers S1, S4 and S2 without fords, at a total cost of 90.

**Final answer:**

The weighted A* plan delivers S1, S2 and S4 without touching any ford, with a total cost of **90**.

**Plan (weighted A*, tunnel_mst heuristic, fords avoided):**
- S1 delivered at step 19
- S4 delivered at step 36
- S2 delivered at step 58
- 58 steps in total: 32 road, 17 grass, 9 mud, and the route uses a teleport tunnel.
- The search expanded 364 nodes.

**Flood status:**
- The rival has not used its dam charge, so no flooding is active (0 flood steps left).
- The current plan has no ford steps, so it is not exposed to a flood.
- The status lists S2 among stops that "need a ford." The plan still reaches S2 without crossing a ford, so that label does not affect this route. It would matter if the route were replanned to allow fords.
- S3 is itself a ford cell. It is not part of this request, so I did not plan for it.

I did not run the simulation, since you only asked for the plan and its flood check.

**Final answer:** The plan delivers S1, S4 and S2 without fords, at a total cost of 90.