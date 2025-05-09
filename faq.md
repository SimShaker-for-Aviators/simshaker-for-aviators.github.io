---
layout: home
title: SimShaker for Aviators
subtitle: Feel the brrrrt!
css: "/assets/css/btn.css"
---

If your question is not answered, please contact me.

## Q: Which network ports uses SSA?
**A:** SSA uses Port **29375 (UDP)** and **12842 (TCP)** to communicate with DCS lua files. For MSFS/FSX is uses SimConnect and for XPlane 11/12 **54930**.
You can use netstat to determine to processes which uses the port
```
netstat -ano  | findstr "12842"
```
You can find the corresponding application with the Windows TaskManager (details page).

## Q: SSA does not connect to DCS?
**A:** SSA uses UPD/TCP to send data to DCS, a firewall or VPN can block this communication, thus check if the traffic is blocked or routed through the VPN.

## Q: Are DCS mods supported by SSA?
**A:** Currently, only official DCS models are supported by SSA.

## Q: A specifiy model/plane/helicopter is not well supported, why?
**A:** Usually I need to buy these models to improve the support. Since this is a hobby project, my budget is very limited. 

## Q: Does SSA conflicts with NRL HFS used for the HF8?
**A:** Yes.
If you decided to use SimShaker for Aviators with DCS and not to use NLR HFS you can resolve this conflict by slightly editing **Export.lua** script in:
```
C:\Users\%username%\Saved Games\DCS\Scripts\
```
NLR HFS inserts its line in this file to engage the script:

```
local HFSlfs=require('lfs');dofile(HFSlfs.writedir()..'Scripts/HFSExport.lua')
```

If you comment this line out by adding -- in front of it as below:

```
--local HFSlfs=require('lfs');dofile(HFSlfs.writedir()..'Scripts/HFSExport.lua')
```
the conflict will be resolved without NLR HFS deletion. 

## Q: Some effects are missing for 3rd party MSFS planes?
**A:** Some planes use custom LVARs, to read these LVARs, please install the *MSFS Bridge* plugin by enabling the checkbox in the *Special Options* tab. 

![MSFS Bridge](assets/img/MSFS_WASM_Bridge.png?raw=true "MSFS Bridge")

Please point the plugin installer to your MSFS community folder. If you use MSFS 2020 and 2024, redo the process for the other simulator. Alternatively, you can copy the *SSA WASM Bridge* plugin folder manually to the other community folder.
