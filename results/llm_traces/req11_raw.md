# Request 11 (raw)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Deliver S1, S2 and S4 without crossing any ford.

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "avoid_terrain": ["ford"], "stops": ["S1", "S2", "S4"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 90.0, "steps": 55, "delivery_order": [{"stop": "S2", "step": 16}, {"stop": "S4", "step": 38}, {"stop": "S1", "step": 55}], "terrain_steps": {"road": 26, "grass": 20, "mud": 9}, "ford_steps": [], "stops": ["S1", "S2", "S4"], "avoid_terrain": ["ford"], "nodes_expanded": 1591, "uses_tunnel": true}`

**Action (Act):** `simulate({"steps": 55})`

**Observation (Sense):** `{"t": 55, "position": [8, 7], "rival": [13, 12], "cost_so_far": 55.0, "delivered": [], "stolen": [], "dam_used": false, "flood_steps_left": 0, "finished": false, "events": []}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": []}`

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "avoid_terrain": ["ford"], "stops": ["S1", "S2", "S4"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 90.0, "steps": 55, "delivery_order": [{"stop": "S2", "step": 16}, {"stop": "S4", "step": 38}, {"stop": "S1", "step": 55}], "terrain_steps": {"road": 26, "grass": 20, "mud": 9}, "ford_steps": [], "stops": ["S1", "S2", "S4"], "avoid_terrain": ["ford"], "nodes_expanded": 1591, "uses_tunnel": true}`

**Action (Act):** `simulate({"steps": 55})`

**Observation (Sense):** `{"t": 110, "position": [8, 7], "rival": [13, 12], "cost_so_far": 110.0, "delivered": [], "stolen": [], "dam_used": false, "flood_steps_left": 0, "finished": false, "events": []}`

**Thought (Reason):** The delivery did not complete, so I can't confirm S1, S2 and S4 were delivered.

**What I did**
- Planned a route with A* (tunnel_mst heuristic) that avoids fords, covering S1, S2 and S4. The plan costs 90 over 55 steps, with no ford steps. The planned order is S2 at step 16, S4 at step 38 and S1 at step 55, using tunnels.
- Ran the plan for 55 steps. The robot ended back at the depot (8, 7) with nothing delivered, nothing stolen, and no events logged. The reported cost was 55, which doesn't match a route that should have moved the robot.
- Re-planned, got the same route, and ran another 55 steps. Same result: at the depot, nothing delivered, cost now 110.
- Flood status shows no dam has been used and no flood is active. Only S2 and S3 are affected by fords, and S3 is itself a ford.

**Status**
- Delivered: none.
- Stolen: none.
- Plan cost for the ford-free route: 90, but the simulator isn't executing it. I stopped after two attempts rather than keep running it.

The likely problem is in the simulator or the way the route is being executed, not in the route itself, since the plan contains no fords. I'd check the execution layer before retrying.

**Final answer:**

The delivery did not complete, so I can't confirm S1, S2 and S4 were delivered.

**What I did**
- Planned a route with A* (tunnel_mst heuristic) that avoids fords, covering S1, S2 and S4. The plan costs 90 over 55 steps, with no ford steps. The planned order is S2 at step 16, S4 at step 38 and S1 at step 55, using tunnels.
- Ran the plan for 55 steps. The robot ended back at the depot (8, 7) with nothing delivered, nothing stolen, and no events logged. The reported cost was 55, which doesn't match a route that should have moved the robot.
- Re-planned, got the same route, and ran another 55 steps. Same result: at the depot, nothing delivered, cost now 110.
- Flood status shows no dam has been used and no flood is active. Only S2 and S3 are affected by fords, and S3 is itself a ford.

**Status**
- Delivered: none.
- Stolen: none.
- Plan cost for the ford-free route: 90, but the simulator isn't executing it. I stopped after two attempts rather than keep running it.

The likely problem is in the simulator or the way the route is being executed, not in the route itself, since the plan contains no fords. I'd check the execution layer before retrying.