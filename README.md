# 🖨️ 3D-Printed Custom Mini-PC TrueNAS Build

![The Final Build](images/corgi3dnas.png)
*Final assembled NAS enclosure (Corgi for scale).*

## 1. Overview & Inspiration
Off-the-shelf NAS boxes are fine if you just want a place to drop files, but I needed something that could actually pull its weight in my homelab. I was looking for a setup capable of handling my general network storage, streaming media through a Jellyfin server, spinning up a few VMs, and acting as a reliable sandbox for my cyber and networking side projects. 

This repository documents how I put together a custom 3D-printed Small Form Factor (SFF) PC running TrueNAS to hit all those marks without blowing my budget. It was an incredibly fun project, and I highly recommend doing a custom build like this yourself—well, *cough cough*, maybe once RAM prices drop. I managed to get my memory right before the current RAM crisis hit, so your mileage on the "budget-conscious" part might vary right now!

**Project Inspiration & Credits:** 
*   **Hardware Haven:** Credit to the YouTube channel Hardware Haven. Their video, [*This 3D-Printed Home Server Is INCREDIBLE*](https://youtu.be/i3G_LvowBkI?si=91bIQ_A8cXWfRrhW), was the main blueprint and motivation to actually pull the trigger on this build. 
*   **Enclosure Design:** The 3D files for the case are the [MASS - Stackable NAS ITX Enclosure](https://modcase.com.au/products/nas?srsltid=AfmBOoqVngkywpRymVcZIYHDWfh9uJF7jblUkSVucGPfCA4IZMH79yzK), which I grabbed from Modcase for $30.00 USD.

---

## 2. Bill of Materials (Hardware & Purchases)
Below is the complete breakdown of all parts utilized for the enclosure fabrication and the internal PC build.

| Category | Item | Purpose / Notes |
| :--- | :--- | :--- |
| **3D Printing** | [Insert 3D Printer Name] | Used to fabricate the main chassis, drive cages, and fan modules. |
| **3D Printing** | [Insert Brand] Beige/Brown PETG | PETG was selected over PLA for superior heat resistance and durability. |
| **3D Printing** | [Link to 3D Plans] | The digital STL files used for slicing and printing. |
| **Case Hardware** | M3 Nuts & Bolts | Used for mounting the motherboard securely without stripping plastic. |
| **Case Hardware** | M3x20 Screws | Used for assembling the primary case halves and drive bays. |
| **Case Hardware** | Standard HDD Screws | Used to secure the 3.5" hard drives into the printed caddies. |
| **PC Components** | [Insert Motherboard/CPU] | The core compute unit for running TrueNAS and managing storage arrays. |
| **PC Components** | [Insert RAM] | Memory required for ZFS caching. |
| **PC Components** | [Insert Power Supply] | [Insert SFX/Flex ATX] form factor to fit the custom chassis footprint. |
| **Storage** | [Insert e.g., 4x WD Blue 4TB HDDs] | Primary storage drives configured in a TrueNAS pool. |
| **Storage** | [Insert Boot Drive / NVMe] | Dedicated OS drive for TrueNAS. |
| **Cooling** | Noctua Low-Profile CPU Cooler | Provided adequate CPU cooling within the tight clearance of the ITX chassis. |
| **Cooling** | [Insert Case Fans, e.g., 140mm] | Primary intake/exhaust to ensure ambient airflow over the storage arrays. |

---

## 3. The Enclosure Fabrication
*Insert any notes here about how long the print took, what slicer settings you used, or any warping issues you had to overcome.*

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
