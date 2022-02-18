WaitForTouchTrigger is a function that stops the scripted sequence until the desired trigger is touched

## Arguments

> **Object: ** Trigger/Part as touching source

## Examples

```lua
WaitForTouchTrigger(Level.TouchTrigger0)
Props.LargeDoor0.Enabled.Value = false
-- closes large door once touched
```

!> **Note:** Higher numbers can cause extreme camera movement, Please use lower numbers instead!
