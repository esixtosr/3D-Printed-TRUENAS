# 🖨️ 3D-Printed Custom Mini-PC TrueNAS Build

![The Final Build](images/corgi3dnas.png)
*Final assembled NAS enclosure (Corgi for scale).*

## 1. Overview & Inspiration
Off-the-shelf NAS boxes are fine if you just want a place to drop files, but I needed something that could actually pull its weight in my homelab. I was looking for a setup capable of handling my general network storage, streaming media through a Jellyfin server, spinning up a few VMs, and acting as a reliable sandbox for my cyber and networking side projects. 

This repository documents how I put together a custom 3D-printed Small Form Factor (SFF) PC running TrueNAS to hit all those marks without blowing my budget. It was an incredibly fun project, and I highly recommend doing a custom build like this yourself—well, *cough cough*, maybe once RAM prices drop. I managed to get my memory right before the current RAM crisis hit, so your mileage on the "budget-conscious" part might vary right now!

**Project Inspiration & Credits:** 
*   **Hardware Haven:** Credit to the YouTube channel Hardware Haven. Their video, [*This 3D-Printed Home Server Is INCREDIBLE*](https://youtu.be/i3G_LvowBkI?si=91bIQ_A8cXWfRrhW), was the main blueprint and motivation to actually pull the trigger on this build. 
*   **Enclosure Design:** The 3D files for the case are the [MASS - Stackable NAS ITX Enclosure](https://modcase.com.au/products/nas?srsltid=AfmBOoqVngkywpRymVcZIYHDWfh9uJF7jblUkSVucGPfCA4IZMH79yzK), which I grabbed from Modcase for $30.00 USD (a free option is available).

---

## 2. Bill of Materials (Hardware & Purchases)
Below is the complete breakdown of all parts utilized for the enclosure fabrication, cooling, internal PC build, and storage array.

| Category | Item | Purpose / Notes |
| :--- | :--- | :--- |
| **3D Printing** | [Flashforge Adventurer 5M](https://a.co/d/00YIra72) | Used to fabricate the main chassis, drive cages, and fan modules. |
| **3D Printing** | [Dark Blue PETG](https://a.co/d/0dnJKtc3) | Main body of the NAS case. (Highly recommend buying 2 spools if you are new to 3D printing to account for misprints!) |
| **3D Printing** | [Black PETG](https://a.co/d/07EWdmw9) | Used specifically for the HDD storage bays for a clean two-tone color aesthetic. |
| **Case Hardware** | [M5 Screws & Bolts Assortment](https://a.co/d/0ja87DbK) | Used for mounting the motherboard securely to the 3D-printed standoffs. |
| **Case Hardware** | [Self-Tapping Case Screws](https://a.co/d/06ilbYNv) | Used to assemble and secure the various 3D-printed case panels together. |
| **Case Hardware** | [Zip Ties](https://a.co/d/00csjYNW) | Absolutely essential for cable management in such a tight ITX enclosure. |
| **PC Components** | [Minisforum Mini-ITX Motherboard/CPU Combo](https://a.co/d/0ctXo52u) | An insane all-in-one embedded board acting as the core compute unit for the server. |
| **PC Components** | [64GB DDR5 SODIMM RAM](https://a.co/d/0aUtl9Gl) | High-capacity memory required to handle ZFS caching, virtualization, and side projects. |
| **PC Components** | [QNAP QM2-2P2G2T Expansion Card](https://www.qnap.com/en/product/qm2-2p2g2t) | A badass find—adds 2x PCIe Gen3 M.2 NVMe SSD slots and 2x 2.5GbE ports to massively upgrade performance and networking. |
| **PSU** | [SFX Modular Power Supply](https://a.co/d/07sb6UsP) | Compact form factor PSU to clean up cable management inside the tiny case footprint. |
| **Accessories** | [16mm Metal Power Button](https://a.co/d/0fBQRLgI) | Plugs into the front panel for a clean, premium power switch. |
| **Cooling** | [Noctua 140mm Premium Fans (x3)](https://a.co/d/0aFWpLIR) | Industrial-grade cooling split up into 3 zones: 1 for the main PC components, 1 at the top to pull out hot exhaust, and 1 dedicated to keeping the HDD storage array chilled. |
| **Storage Controller** | [M.2 NVMe to SATA Adapter](https://a.co/d/0b52Osdg) | Crucial addition to add SATA connections for the hard drives, since the Minisforum motherboard only has NVMe slots. |
| **Storage (Boot)** | [256GB NVMe SSD](https://a.co/d/0hwbGVMs) | Dedicated boot drive for the host OS (Proxmox/TrueNAS). |
| **Storage (Fast)** | [Samsung EVO 1TB NVMe SSD (x2)](https://a.co/d/05a3ng1z) | Fast NVMe storage pool dedicated to running VMs and handling high-speed processing tasks. |
| **Storage (Bulk)** | [1TB 3.5" HDD (x2)](https://a.co/d/09LaWEtu) | Drives I had laying around, primarily used for my Jellyfin media library (movies/shows) and bulk project storage. |
| **Storage (Misc)** | [1TB 2.5" HDD (x3)](https://a.co/d/05E49N7L) | Extra drives I had laying around, slotted in for general storage pools or whatever random side projects pop up. |

---

## 3. The Enclosure Fabrication
If you take nothing else away from this build, let it be this: **PETG = SLOW PRINTS. Patience is key.**

I chose PETG over PLA (as suggested in the inspiration video) because it offers much better heat resistance, which is absolutely mandatory when you are cramming spinning hard drives and a CPU into a tiny plastic box. However, if you have never printed PETG before, definitely look up some tutorials first.

Here are my specific notes and slicer settings using **Orca Slicer**:
* **Print Speeds:** I had to drop my speeds drastically to get clean layers. Keep your overall speed between **40–55 mm/s max**. For the few tiny supports you actually need, drop the speed all the way down to **15–20 mm/s**.
* **Temperatures:** Always read the manual for your specific filament brand, but I found the sweet spot to be around **235–255°C for the nozzle** and **75–85°C for the build plate**.
* **Dry Your Filament:** PETG absorbs moisture from the air like a sponge. If your filament is wet, it will string everywhere and your layers will be weak. Use a filament dryer or print straight out of a dry box if you can.
* **Structural Integrity:** Spinning hard drives create vibration, and power supplies are heavy. As noted in the included Modcase manual, make sure you use at least 4 wall loops for strength. Also, **print the rear panel at 100% infill**—it bears the weight of the PSU and needs to be rock solid.
* **Bed Adhesion:** PETG sticks *really* well. Sometimes too well. If you are using a smooth PEI or glass bed, use a dedicated 3D print glue (not just any standard craft glue stick). It acts as a release agent so the PETG doesn't rip chunks out of your build plate. 
* **Let It Cool!** I learned this one the hard way. Once a print finishes, leave it on the plate for at least **30 minutes** to cool down. If you try to pull it off while it is still warm, the parts will warp and bend, and you will be stuck reprinting them. 

Take your time with this phase. Printing the chassis is by far the most time-consuming part of the entire project, but doing it right the first time saves a massive amount of headache later.

## 4. PC Assembly & Configuration
![Internal Layout](images/IMG_2939.png)
*Motherboard mounting and Noctua cooler clearance.*

*   **Internal Assembly:** *Talk about fitting the motherboard, routing the power cables, and any tight clearances.*
*   **Drive Installation:** *Explain how the drives slide into the rear of the enclosure.*

![Rear I/O and Drive Bays](images/IMG_2923.png)
*Rear view showcasing the exposed drive bays, I/O shield, and power supply mount.*

## 5. Final Thoughts & Lessons Learned
*   What was the hardest part of the physical build? 
*   Did you run into any heat or clearance issues once TrueNAS was booted up and the drives were spinning?
