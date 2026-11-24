# Request 12 (validated)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Deliver S1 while avoiding grass.

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "stops": ["S1"], "avoid_terrain": ["grass"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 36.0, "steps": 25, "delivery_order": [{"stop": "S1", "step": 25}], "terrain_steps": {"road": 22, "mud": 2, "ford": 1}, "ford_steps": [21], "stops": ["S1"], "avoid_terrain": ["grass"], "nodes_expanded": 104, "uses_tunnel": false}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": [21]}`

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "stops": ["S1"], "avoid_terrain": ["grass", "ford"]})`

**Observation (Sense):** `{"ok": false, "error": "no route found (search failed)", "expanded": 101}`

**Action (Act):** `simulate({"steps": 25})`

**Observation (Sense):** `{"t": 25, "position": [8, 7], "rival": [13, 12], "cost_so_far": 25.0, "delivered": [], "stolen": [], "dam_used": false, "flood_steps_left": 0, "finished": false, "events": []}`

**Action (Act):** `plan_route({"algorithm": "astar", "heuristic": "tunnel_mst", "stops": ["S1"], "avoid_terrain": ["grass"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 36.0, "steps": 25, "delivery_order": [{"stop": "S1", "step": 25}], "terrain_steps": {"road": 22, "mud": 2, "ford": 1}, "ford_steps": [21], "stops": ["S1"], "avoid_terrain": ["grass"], "nodes_expanded": 104, "uses_tunnel": false}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": [21]}`

**Action (Act):** `simulate({"steps": 25})`

**Observation (Sense):** `{"t": 50, "position": [8, 7], "rival": [13, 12], "cost_so_far": 50.0, "delivered": [], "stolen": [], "dam_used": false, "flood_steps_left": 0, "finished": false, "events": []}`

**Action (Act):** `simulate({"steps": 1})`

**Observation (Sense):** `{"t": 51, "position": [8, 7], "rival": [13, 12], "cost_so_far": 51.0, "delivered": [], "stolen": [], "dam_used": false, "flood_steps_left": 0, "finished": false, "events": []}`

**Thought (Reason):** I did not deliver S1. The robot is still at the depot (8, 7) with nothing delivered, and its cost has climbed to 51 without any movement.

**What I did:**
- **Plan:** A* with the tunnel-aware MST heuristic, avoiding grass. It found a 25-step route to S1 (21, 5) with total cost 36: 22 road steps, 2 mud steps, and 1 ford step at step 21.
- **Ford check:** I tried a route avoiding both grass and fords, and no route exists. The ford crossing is unavoidable for S1.
- **Flood status:** The rival has not used its dam, so no fords are currently flooded.
- **Execution:** I simulated 25 steps, then another 25, then 1 more. Each time the robot reported the same position, (8, 7), with no events, while cost kept accumulating. The re-plan returned the same route each time.

**Status:** Nothing has moved, so the stall is not explained by the route itself. I'd check the robot's movement or slip handling before retrying. If you want, I can try a different algorithm (for example UCS or greedy) to see whether the stall is specific to this search.

**Plan cost (intended route):** 36, not yet achieved.

**Final answer:**

I did not deliver S1. The robot is still at the depot (8, 7) with nothing delivered, and its cost has climbed to 51 without any movement.

**What I did:**
- **Plan:** A* with the tunnel-aware MST heuristic, avoiding grass. It found a 25-step route to S1 (21, 5) with total cost 36: 22 road steps, 2 mud steps, and 1 ford step at step 21.
- **Ford check:** I tried a route avoiding both grass and fords, and no route exists. The ford crossing is unavoidable for S1.
- **Flood status:** The rival has not used its dam, so no fords are currently flooded.
- **Execution:** I simulated 25 steps, then another 25, then 1 more. Each time the robot reported the same position, (8, 7), with no events, while cost kept accumulating. The re-plan returned the same route each time.

**Status:** Nothing has moved, so the stall is not explained by the route itself. I'd check the robot's movement or slip handling before retrying. If you want, I can try a different algorithm (for example UCS or greedy) to see whether the stall is specific to this search.

**Plan cost (intended route):** 36, not yet achieved.