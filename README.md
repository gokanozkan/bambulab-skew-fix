# [FIXED] Skewed prints in XY after firmware update (works for all models)

Hi all,

I wanted to share a solution for a **skew issue I had on my P1S after a firmware update**.  
> I use a **P1S**, but this could apply to **any BambuLab printer** that uses automatic skew correction — including **P1P, X1C, X1E, A1 Mini**, etc.

---

## 🧩 Symptoms:
- Purge line was **skewed**, noticeably closer to the right side of the bed  
- Printhead wasn’t moving in **clean straight lines**, especially when going to the poop chute  
- **Gantry shifted front-to-back** during side-to-side motion  
- Weird purge behavior: nozzle temp dropped in steps and pooped multiple times  

At first I suspected a mechanical issue, but everything looked solid.  
I then looked into **firmware-level skew calibration**.

---

## 🛠️ What worked for me:

I created a G-code file with the following lines and ran it via SD card (no console access):

```gcode
M1005 I0        ; reset the skew compensation values  
M990 Skew_Clear  
M991 Skew_Calibrate  
M500            ; save the new calibration
