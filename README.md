This project designed autonomous agents to compete or work collaboratively with each other in a predefined environment.

_MASSim_ simulations run in discrete steps. Agents connect remotely to the
contest server, receive percepts and send their actions, which are in turn
executed by _MASSim_.

<p align="center">
  <img src="https://multiagentcontest.org/2019/banner.png">
</p>




The code is organized around a hierarchical decision framework:
!do_action → !submit_task → !exchange_info → !attach_block → !request_block → !go_to_dispenser → !move_random

This design ensures that agents set higher priority on behaviours such as delivering tasks before attempting lower-value actions like random exploration. The next applicable plan will automatically be tried if the current goal cannot be met due to missing conditions.
Leader and follower roles appear during coordination depending on the relative positions between agents and other factors. 

Rather than selecting any available task at random, the agent evaluates task utility before submission. This favours tasks with higher rewards and those whose deadlines are approaching, improving the efficiency. When a task is received, the program extracts the block requirements and stores them in a belief format. Task utility is computed by:
Utility = (Reward × 100) / (Deadline − CurrentStep)

Without a proper pathfinding strategy, agents occasionally oscillate in dense areas. Relying on local heuristics only guides the agents toward targets using relative offset rather than calculating the most optimal paths. By not having proper role assignment, the agents sometimes compete for the same dispensers rather than distributing tasks effectively. The coordination protocol is sensitive to step synchronisation





Download
--------

Clone this repository (or download it as zip).

License
-------

_MASSim_ is licensed under the AGPLv3+. See COPYING.txt for the full
license text.
