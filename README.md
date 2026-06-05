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
* **TPU Feet for Shock Absorption:** The manual recommends printing the case feet out of flexible TPU to help absorb vibrations from the spinning hard drives. I actually skipped this and used PETG because my unit sits on the carpet. (I know, I know, airflow—but the case panels and Noctua fans keep the dust away surprisingly well!). However, if you are putting this on a hard wooden desk, definitely use TPU for the feet to kill the vibration noise.

Take your time with this phase. Printing the chassis is by far the most time-consuming part of the entire project, but doing it right the first time saves a massive amount of headache later.

---

## 4. PC Assembly & Configuration
As outlined in the Modcase manual, the physical build is divided into three distinct sections: the **Top Cover**, the **Main Body** (where the PC components live), and the **Base** (the HDD storage array). Overall, everything fits together perfectly like a puzzle piece, and it is a genuinely fun project to build. Just don't rush it.

![Internal Layout](images/IMG_2939.png)
*Motherboard mounting and internal cable management.*

*   **The Top Cover & The "Fan Mistake":** Let's get this out of the way first. You **MUST** install the exhaust fan into the top module *before* screwing the top cover onto the case. The guy in the Hardware Haven video made this mistake, and so did I. If you forget, you have to completely disassemble the top half of the case to get the fan in. Also, the top cover attaches using the self-tapping M3 screws, not the M3 nuts/bolts kit. An extended screwdriver bit helps here, but I managed fine without one.
*   **Main Body Assembly:** The motherboard and SFX power supply drop in and screw down quite nicely. The PSU cables will be a very tight fit, so utilize your zip ties and cable manage as much as you can right from the start.
*   **The NVMe-to-SATA Adapter:** Be extremely careful with this component. The adapter board is quite flimsy. When plugging in or unplugging SATA cables, support the board with your fingers so you don't accidentally snap or bend the connector.
*   **Storage Bays & Cabling:** Routing the SATA and power cables down into the HDD base is visually a bit of a mess, but they reach without any clearance issues. Note that if you are using 2.5" HDDs, they require an additional printed attachment to secure them into the 3.5" bays.
*   **A Note on SATA Cables:** I used the SATA cables that came included with the NVMe adapter, but they tend to slip off easily. I highly recommend buying higher-quality locking SATA cables for a more secure connection.

![Rear I/O and Drive Bays](images/IMG_2939.png)
*Rear view showcasing the exposed drive bays, I/O shield, and power supply 

*   **Internal Assembly:** *Talk about fitting the motherboard, routing the power cables, and any tight clearances.*
*   **Drive Installation:** *Explain how the drives slide into the rear of the enclosure.*

![Rear I/O and Drive Bays](images/IMG_2923.png)
*Rear view showcasing the exposed drive bays, I/O shield, and power supply mount.*

## 5. Final Thoughts & Lessons Learned
This 3D-printed NAS was a massive milestone for my homelab setup. My comfort zone is usually on the software and configuration side of things—setting up network segmentation, managing Active Directory domains, or spinning up VMs. Forcing myself to physically engineer and troubleshoot the hardware enclosure from scratch was an incredible learning curve. 

**Key Takeaways:**
*   **Hardware Tolerances are Unforgiving:** A software bug can usually be patched in seconds. If a PETG panel warps by two millimeters after a 14-hour print, you are starting over from scratch. I gained a huge appreciation for physical hardware limitations and thermal management.
*   **The Bare-Metal Foundation:** You cannot fully secure or effectively virtualize an environment without understanding the physical layer first. Working around motherboard limitations by adding the QNAP expansion card and M.2 adapters reinforced how underlying hardware bottlenecks directly dictate your software and network capabilities.
*   **SFF is Shockingly Capable:** The Minisforum board combined with the right expansion components proved that you do not need a massive, power-hungry desktop tower to run a highly capable virtualized environment.
*   **True Modularity and Ownership:** Off-the-shelf NAS appliances are easy, but they lock you into their proprietary hardware and ecosystems. By fabricating the enclosure myself and cherry-picking every component, I have 100% control over the system's lifecycle. If a drive bay cracks or I want to adapt it for more drives, I don't have to buy a whole new appliance—I just boot up the 3D printer.

**What is Next? (Infrastructure Scaling)**
While this custom NAS has been an absolute beast for handling my Jellyfin media library and hosting my initial sandbox VMs, my infrastructure needs have officially outgrown it. The next step is scaling up and bringing everything I have learned over the last four years together into one unified, secure environment. 

Moving forward, the focus shifts from basic storage to tackling more complex topics like advanced security implementations, intricate network topologies, and managing heavier virtualization loads. This project proved I could bootstrap a stable environment from the ground up; the next evolution is taking all those concepts and migrating them into a dedicated, on-premise server rack. You can check out that migration in my main portfolio timeline!
