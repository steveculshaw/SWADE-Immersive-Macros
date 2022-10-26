As of version 1.0.0 SWIM started introducing custom Active Effect strings that can be set up on actors and will then alter the rolls made by SWIM. Note that SWIM already is aware of many Edges and Hindrances, when performing rolls in SWIM so there is no need to set up Active Effect for those.

## Unstun Modifier
This will add a generic modifier to rolls made when attempting to shake off the effects of being Stunned.
To use it create an active effect with the attribute key `SWIM.unStunMod` (case sensitive), the change mode `Add` and a value of your choosing. A bonus must not have a `+` in front of the number, a penalty needs a `-` in front of the number.