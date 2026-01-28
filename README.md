# TI Webench Power Designer generated buck converter  
  
  
Have you ever needed a buck converter for a desk prototype and then found out that the particular IC intended for the target design has no evaluation kit? Same here. After generating a buck converter design with the desired parameters in [Texas Instruments WEBENCH® Power Designer](https://webench.ti.com/power-designer/), the next step was to test a physical device. Going a bit crazy (and lazy), the schematic and layout were exported and produced as-is. This README describes how it went.  
##   
##   
## Requirements  
* Vin min = 18 V  
* Vin max = 26 V  
* Vout = 12 V  
* Iout = 8 A  
##   
##   
## Texas Instruments Power Designer project  
  
Getting a design in [Texas Instruments WEBENCH® Power Designer](https://webench.ti.com/power-designer/) is as easy as providing requirements and choosing a ready design from the list. In the generated PDF report, all components are already selected with corresponding MPNs.  
  
  
![Screenshot 2025-11-23 at 18.52.15.png](Attachments/D5F0EDDD-8CBC-4EF2-B04A-5BA9FE69D230.png)  
  
Got the complete schematic of the buck converter:  
![Screenshot 2026-01-28 at 17.44.16.png](Attachments/CCAE6240-8D29-4377-A7C9-0BDD5B67C6E5.png)  
  
With parametrics as efficiency at various load currents:  
  
![amCharts (1).png](Attachments/7DD8723A-D6BE-4404-8587-907C3ECE146C.png)  
  
  
## Project imported to Altium  
  
Going straight to the point of this test: the project was exported from the tool and imported into [Altium Designer](https://www.altium.com/altium-designer). During import, Altium only asked whether to convert the ASCII file to a binary format. After that, both the schematic and the board layout were available.  
  
![Zrzut ekranu 2025-11-24 085329.png](Attachments/C3281C94-601F-49D6-9A89-502695B6CEA7.png)  
  
### Schematic
  
The schematic looked good right away—each component even had its MPN.  
  
![Screenshot 2026-01-27 at 20.24.20.png](Attachments/12BFF772-A99C-4678-A87C-68D3B7E81D6A.png)  
  
### Layout
  
On the layout, on the other hand, I found a few glitches. All silkscreen elements were poorly positioned.  
  
![Zrzut ekranu 2025-11-24 092811.png](Attachments/06E774BB-B332-49A3-8D37-022C1488A42D.png)  
  
In the board layout found a few weird routings:  
  
![Zrzut ekranu 2025-11-24 084827.png](Attachments/12FD00D0-6EF6-48B7-A551-BB4BD2B3C5A9.png)  
  
![Zrzut ekranu 2025-11-24 084753.png](Attachments/A00C46CC-1AAE-4B3E-B2FE-E9519337CD06.png)  
![Zrzut ekranu 2025-11-24 084744.png](Attachments/1F122C1F-DC85-4EEC-81BA-A450118B67D0.png)  
  
And even a short:  
  
![Zrzut ekranu 2025-11-24 084317.png](Attachments/C54FF4E8-4E69-41E4-9218-35F43C5B7DF6.png)  
  
But apart from those issues, for an automatically generated layout it looks quite good overall. Worth mentioning that after import all copper planes are copper fills rather than polygons, so they will not easily repour to avoid shorts.  
  
  
After a few corrections, the board looks like:  
  
  
![Screenshot 2026-01-27 at 20.24.51.png](Attachments/212E1CE2-AF36-4523-BFCE-886412F31501.png)  
![Screenshot 2026-01-27 at 20.24.54.png](Attachments/55CC68D7-03F7-49B1-97EE-4F285DEDA8B2.png)  
![Screenshot 2026-01-27 at 20.24.56.png](Attachments/70574390-429B-4F2D-A88B-99EF0CD216EE.png)  
(On the in.2 Vout sense signal is shorted at vias, right before output terminal - this small short was missed before ordering)  
![Screenshot 2026-01-27 at 20.24.58.png](Attachments/FAE047A6-F8CF-4810-8753-E634C89E4897.png)  
  
### 3D view 
  
![SYNCOUT](Attachments/13E8881F-DC4E-4B67-8DB4-A0EAFC90DFA1.png)  
![Screenshot 2026-01-27 at 20.17.19.png](Attachments/FD8707D4-D405-4837-9952-F62573A5BF8A.png)  
  
  
## Ordered PCBs  
  
PCBs ordered on JLCPCB and hand soldered:  
  
![IMG_8076.jpeg](Attachments/19D54B30-E4DA-4CEC-9DA4-65197882EB39.jpeg)  
  
### Assembled board 
  
![IMG_8082.jpeg](Attachments/9532E7A9-6322-43AC-9117-736D2376EA06.jpeg)  
  
  
## Bring-up and tests  
  
Bring-up was rather quick—connected a lab bench power supply set to 19 V to VIN and GND and… it worked. 12.3 V on the output. I was surprised. I did not even open the application note for that buck converter once.  
  
  
## Testing under load:  
  
Made quick test under load before putting into the prototype. For that used some cheap non branded active load.   
  
### At 4A load:  
  
![20260128T195555.jpg](Attachments/FC9C7347-0D12-4F5B-BA2F-7853DC45C167.jpg)  
  
### 5 minutes of operation at 4A load timelapse:  
  
![4a GIF](Attachments/4A.gif) 

  
### At 8A load:  
![20260128T201047.jpg](Attachments/78BE8306-4796-42CB-96CB-8BF0ABE52A4C.jpg)  
  
  
### 5 minutes of operation at 8A load timelapse:  
  
  ![8a GIF](Attachments/8A.gif) 
  
Efficiency was intentionally not measured, as even on the thermal camera it was clear the cables were getting hot, and most of the losses may be caused by poor, too-thin cables.  
  
  
## Vin and Vout measurements on the oscilloscope  
  
### At 4A load:  
  
![RigolDS117.png](Attachments/EA944A67-B500-49D5-96B8-940A0E267488.png)  
  
  
### At 8A load:  
  
![RigolDS123.png](Attachments/47C2E811-8107-4E01-83C9-D92F4D730F66.png)  
  
![RigolDS126.png](Attachments/CEFAB7E9-5EDB-4816-9280-4356029A4F91.png)  
  
  
## Summary:  
  
Actually I’m pretty surprised by this automatically generated design. It works. The datasheet was not opened. Generate the design, make slight corrections in [Altium Designer](https://www.altium.com/altium-designer), order the PCB, assemble it, and just power it up. The layout is quite good, and the PCB area is sufficient for the power converter to work without overheating. [Texas Instruments WEBENCH® Power Designer](https://webench.ti.com/power-designer/) will definitely be used in the future and can be recommended.  
