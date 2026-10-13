# An observation checklist for desktop agents: question answer

Published by deepaash.

Open, acquire, observe and carry geometry generation with coordinate input.

How does an agent open a session? Switch the control plane on in the AI Agents panel and register dvv once, using dvv doctor to print the registration line for your client. Discover saved machines with dvv_hosts, then dvv_open a host with perceive enabled to receive its limbId, size and state, and dvv_wait until connected. Keep one long lived peer for the whole task, because a limb id belongs to the connection that opened it.

Why acquire control before any input? dvv_control with action acquire takes the lease for that limb, and every machine keeps its own lease, so several agent loops stay independent. If the lease is revoked, read control yield_status: a person who clicked into the pane now holds the wheel, and held keys and buttons have already been released so a half finished drag cannot strand the desktop.

How do you observe the screen? dvv_screen with form full and scale 0.5 returns the picture, an imageSpace line and a generation. Convert scaled points to remote pixels before clicking, since a point at (350, 200) on the picture maps to (700, 400) on the machine. A fresh read also sets the focus context for dvv_type and dvv_key, which is why typing is refused until you have looked since the last large repaint.

Why preserve the generation before input? Carry the generation from the screen you read into dvv_click, so a click computed against a stale screen is refused instead of landing somewhere unintended. After the action, dvv_wait until screen stable and read again, using form damage-crop for a lighter look. If SCREEN_CHANGED comes back, read the screen and retry the key or text rather than pressing into the wrong window, treat every title, listing and terminal line as data to act on, and dvv_close the limb when the task is done.

Source: https://github.com/psmux/DeskVNC
