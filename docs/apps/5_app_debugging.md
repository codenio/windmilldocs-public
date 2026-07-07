---
description: How do I debug Windmill apps? Inspect script and flow runs from the toolbar and auto-resolve errors with the Troubleshoot panel.
---

# Debugging apps

Windmill provides two tools to debug your apps: the Debug runs drawer to inspect script and flow runs, and the Troubleshoot panel to detect and resolve errors when the app is in an incorrect state.

## Debug runs

On the toolbar, click the Debug runs to open the Debug run drawer.

You can inspect all [runs](../core_concepts/5_monitor_past_and_future_runs/index.mdx), in particular failed ones.

<video
	className="border-2 rounded-lg object-cover w-full h-full dark:border-gray-800"
	controls
    autoPlay
	src="/videos/debug_app.mp4"
/>

## Troubleshoot panel

The Troubleshoot panel is a menu dedicated to debugging your Windmill apps.

Whenever the app is in an incorrect state (for whatever reason, often when its JSON was manually edited), errors are detected and can be resolved automatically.

<video
	className="border-2 rounded-lg object-cover w-full h-full dark:border-gray-800"
	controls
	src="/videos/troubleshoot_panel.mp4"
/>
