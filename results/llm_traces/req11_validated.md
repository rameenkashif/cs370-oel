# Request 11 (validated)

Rameen Kashif (456834) | Manal Aslam (465734) | Zainab Ali Bangash (486688)

> Deliver S1, S2 and S4 without crossing any ford.

**Action (Act):** `plan_route({"algorithm": "astar", "avoid_terrain": ["ford"], "heuristic": "tunnel_mst", "stops": ["S1", "S2", "S4"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 90.0, "steps": 55, "delivery_order": [{"stop": "S2", "step": 16}, {"stop": "S4", "step": 38}, {"stop": "S1", "step": 55}], "terrain_steps": {"road": 26, "grass": 20, "mud": 9}, "ford_steps": [], "stops": ["S1", "S2", "S4"], "avoid_terrain": ["ford"], "nodes_expanded": 1591, "uses_tunnel": true}`

**Action (Act):** `simulate({"steps": 55})`

**Observation (Sense):** `{"t": 55, "position": [8, 7], "rival": [13, 12], "cost_so_far": 55.0, "delivered": [], "stolen": [], "dam_used": false, "flood_steps_left": 0, "finished": false, "events": []}`

**Action (Act):** `flood_status({})`

**Observation (Sense):** `{"dam_used": false, "flood_steps_left": 0, "flood_duration": 15, "stops_that_need_a_ford": ["S2", "S3"], "stop_cells_that_are_fords": ["S3"], "current_plan_ford_steps": []}`

**Action (Act):** `plan_route({"algorithm": "astar", "avoid_terrain": ["ford"], "heuristic": "tunnel_mst", "stops": ["S1", "S2", "S4"]})`

**Observation (Sense):** `{"ok": true, "algorithm": "astar", "heuristic": "tunnel_mst", "cost": 90.0, "steps": 55, "delivery_order": [{"stop": "S2", "step": 16}, {"stop": "S4", "step": 38}, {"stop": "S1", "step": 55}], "terrain_steps": {"road": 26, "grass": 20, "mud": 9}, "ford_steps": [], "stops": ["S1", "S2", "S4"], "avoid_terrain": ["ford"], "nodes_expanded": 1591, "uses_tunnel": true}`

**Action (Act):** `simulate({"steps": 55})`

**Observation (Sense):** `{"t": 110, "position": [8, 7], "rival": [13, 12], "cost_so_far": 110.0, "delivered": [], "stolen": [], "dam_used": false, "flood_steps_left": 0, "finished": false, "events": []}`

**Thought (Reason):** I couldn't complete the delivery. The robot is back at the depot (8, 7) with no stops delivered, and I've stopped rather than keep running it.

**What happened:**
- The route planner found a ford-free plan: A* with the tunnel_mst heuristic, avoiding fords, cost 90 over 55 steps. Delivery order was S2 at step 16, S4 at step 38, S1 at step 55. It used tunnels and no fords.
- I ran that plan for 55 steps. The robot ended at the depot with cost 55, nothing delivered, and no events logged.
- I checked flood status: no dam has been used and no flood steps remain. The ford stops are S2 and S3 per the status report, but S2 and S3 are not in the ford-free plan's path.
- I replanned from the depot. The planner returned the same 90-cost plan, and running it for another 55 steps again left the robot at the depot with nothing delivered. The total cost so far is 110, with no progress.

The planner's route is valid on paper, but execution does not move the robot toward the stops. I can't see the cause from these tools. It could be a fault in how the plan is executed, or in how the simulator handles the tunnels.

**Options:**
1. Try a different algorithm (e.g., UCS or BFS with the same ford avoidance) and see whether execution behaves differently.
2. Deliver one stop at a time (e.g., S2 first) to find where the movement stalls.
3. Stop here and investigate the simulator.

The ford-free delivery of S1, S2 and S4 is feasible on the planner's side, with a planned cost of 90. The actual execution has not succeeded so far.

**Final answer:**

I couldn't complete the delivery. The robot is back at the depot (8, 7) with no stops delivered, and I've stopped rather than keep running it.

**What happened:**
- The route planner found a ford-free plan: A* with the tunnel_mst heuristic, avoiding fords, cost 90 over 55 steps. Delivery order was S2 at step 16, S4 at step 38, S1 at step 55. It used tunnels and no fords.
- I ran that plan for 55 steps. The robot ended at the depot with cost 55, nothing delivered, and no events logged.
- I checked flood status: no dam has been used and no flood steps remain. The ford stops are S2 and S3 per the status report, but S2 and S3 are not in the ford-free plan's path.
- I replanned from the depot. The planner returned the same 90-cost plan, and running it for another 55 steps again left the robot at the depot with nothing delivered. The total cost so far is 110, with no progress.

The planner's route is valid on paper, but execution does not move the robot toward the stops. I can't see the cause from these tools. It could be a fault in how the plan is executed, or in how the simulator handles the tunnels.

**Options:**
1. Try a different algorithm (e.g., UCS or BFS with the same ford avoidance) and see whether execution behaves differently.
2. Deliver one stop at a time (e.g., S2 first) to find where the movement stalls.
3. Stop here and investigate the simulator.

The ford-free delivery of S1, S2 and S4 is feasible on the planner's side, with a planned cost of 90. The actual execution has not succeeded so far.