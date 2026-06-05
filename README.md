# 🖨️ 3D-Printed Custom Mini-PC TrueNAS Build

![The Final Build](images/corgi3dnas.png)
*Final assembled NAS enclosure (Corgi for scale).*

## 1. Overview & Inspiration
I needed a reliable, budget-conscious storage solution for homelab backups and media, but I wanted something more customizable than an off-the-shelf appliance. This project documents the design, assembly, and configuration of a custom 3D-printed Network Attached Storage (NAS) unit powered by a Small Form Factor (SFF) PC running TrueNAS.

**Project Inspiration & Credits:** 
*   **Hardware Haven:** A massive shout-out to the YouTube channel Hardware Haven. Their video, *"This 3D-Printed Home Server Is INCREDIBLE,"* served as the primary blueprint and inspiration for this build. 
*   **Enclosure Design:** The 3D models and plans used for this build were purchased from [Insert ModCase or Creator Link Here]. 

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
