---
Title: "Cat Board Keyboard"
Author: "Hewis"
Description: "Everyone’s using stock layouts, imma build my own 65% with OLED and hot‑swap"
created_at: "2025-07-13"
Total time spent: 20
---

## July 13 – Ideation and Initial Schematic (7 hours)

It all began late on the night of July 12, when I was deep into marathon coding and suddenly paused to sip my lukewarm masala chai. My old membrane keyboard skull‑rattled under my fingers and felt like I was typing on jello. The keys were mushy, the function row was buried two layers deep in my software, and there was no quick way to adjust volume or see which layer I was on. In that moment, frustration morphed into inspiration: “Yaar, I need something of my own. A custom board that’s smart, tactile, and packed with just the right features.” With that spark, **Cat Board** was born.



![WhatsApp Image 2025-07-13 at 17 15 58_e7780501](https://github.com/user-attachments/assets/04ae023a-6590-4316-9061-8a62b9881138)




## Say Hello to my CAT- OREO 






I cleared my desk, grabbed a fresh notebook, and started sketching in pen. My vision was a classic 65 percent layout that gives room for dedicated arrow keys and a small cluster of navigation keys without eating too much desk real estate. Next, I doodled two rotary encoders at the top right corner—one for volume control and the other for scrolling through endless blocks of code—and then a little window in between for a 0.91‑inch OLED screen. That tiny display would show the current layer, a simple clock, or even a playful pixel art cat when idle. A cat theme seemed fitting, since I often find myself procrastinating by watching my own cat sleep.

By 2 AM, I had three pages of rough sketches: row and column counts, encoder placements, OLED dimensions, USB‑C port location, and hot‑swap footprints for sixty‑one switches. It felt like designing a mini cockpit for my fingers. The next step was to turn those sketches into a real schematic, so I fired up EasyEDA and created a new project titled “Cat Board.”

First, I placed the **Arduino Pro Micro** clone footprint at the bottom center—this microcontroller is battle‑tested for QMK and can handle USB‑C breakout circuits easily. I wired decoupling capacitors—100 nF each—directly across VCC and GND pins to suppress noise, and added ESD diodes on the USB data lines just in case. I then set up the **switch matrix**: seven columns by nine rows, each switch slot bridged by a 1N4148 diode to prevent ghosting. The nets were named row0 through row8 and col0 through col6. Seeing the matrix appear on my screen matched the excitement of watching a blueprint come to life.


<img width="858" height="623" alt="image" src="https://github.com/user-attachments/assets/5a0738bc-dfcf-4500-ac41-f2ec17ef7b3c" />







Next, I dropped in footprints for the **rotary encoders**: EC11‑style with integrated push switches. Each encoder required two GPIOs for quadrature signals and one for the push‑button . The encoder symbols were placed to the right of the switch grid, and I drew connections as thin lines, careful not to cross nets prematurely.



<img width="478" height="182" alt="image" src="https://github.com/user-attachments/assets/c1ee8a82-4eb5-4835-9ff8-73ccc932fe97" />








Then, I added the **0.91″ OLED module** footprint between the two encoders, marking its I²C SDA and SCL pins. I included the two required 10 kΩ pull‑up resistors on those lines, and labeled nets `SDA` and `SCL`. I also sketched in the 3.3 V power pin and GND. A net tie ensured the display’s ground plane would join the board’s main ground.



<img width="478" height="226" alt="image" src="https://github.com/user-attachments/assets/85bc73d4-b059-4871-8ec0-6e5e2b7b5b5e" />





By 4 AM, the schematic diagram was complete: Pro Micro clone, switch matrix with diodes, encoder circuits with pull‑ups and debounce caps, OLED interface, ESD protection, and decoupling. Every symbol was meticulously named and the overall sheet felt intuitive. I double‑checked the power rails, verified every net connection, and ran the ERC (Electrical Rule Check)—no errors. There it was: the brain of Cat Board, captured in schematic form.





<img width="975" height="621" alt="Screenshot 2025-07-13 190219" src="https://github.com/user-attachments/assets/e450120f-925e-419f-bbc5-455c9116c614" />







With pride and bleary eyes, I saved my work and shut down my computer at around 5 AM. The foundational blueprint for Cat Board was set, and I knew the next day would involve translating this into a physical PCB layout—a challenge I was eager to tackle.

---

## July 14 – PCB Layout and Routing  (8.5 hours)

I woke up around noon on July 14, feeling surprisingly refreshed after a short nap and another cup of strong masala chai. My mission for Day 2: tame the beast of PCB layout and routing within EasyEDA’s PCB editor. I imported my schematic netlist, and instantly saw the unplaced footprints floating on the tarmac of a 295 × 100 mm board outline—the exact dimensions for a 65% keyboard.



<img width="1061" height="501" alt="image" src="https://github.com/user-attachments/assets/660be024-49ea-4c9d-ac6b-381a96f3be84" />





### Component Placement

I began by dropping the **Pro Micro** clone onto the bottom middle area, orienting its USB‑C pads towards the front edge. I drew a guide rectangle showing where the case cutout would be so I wouldn’t block the connector. Above it, I placed the **OLED** footprint, leaving a 12 mm cutout zone for the display window. To its right, I positioned the two **rotary encoders**, spaced 24 mm apart to match the diameter of standard encoder knobs and to clear adjacent keycaps. At this stage, it felt like arranging furniture in a very cramped apartment.


<img width="1048" height="515" alt="image" src="https://github.com/user-attachments/assets/28d56242-01d5-401a-93be-8799b594b852" />





Next, I laid out the **switch footprints** in a staggered matrix: seven columns of nine rows, plus two extra keys on the rightmost column for the Function and Menu keys. Each footprint had pad pairs for a hot‑swap socket beneath, with mounting holes around them sized for the socket’s pins. I used the drag‑and‑drop grid settings to align everything precisely, checking edge clearance for the case later.

### Routing Strategy

With placements set, I shifted to the **Routing** tool. I decided to route power rails first: 24 mil traces for VCC from the USB‑C 5 V pad branching out around the left and right edges, and a 24 mil ground trace creating a continuous loop under the Pro Micro footprint. Then I poured a copper ground plane on both top and bottom layers, leaving isolation gaps around signal traces.

I tackled the **switch rows** on the top layer next, setting trace width to 10 mil. Each row net snaked across the board, hugging the spaces between switch pads. When I hit congestion near the encoders, I zoomed in, nudged footprints by fractions of a millimeter, and re‑routed. The columns were planned for the bottom layer, so I switched layers and began routing col0 through col6 with 10 mil traces. Each time I needed to jump layers, I placed 0.6 mm vias, ensuring drill spec compliance.


<img width="1042" height="467" alt="Screenshot 2025-07-13 154307" src="https://github.com/user-attachments/assets/bb187c81-aa27-4088-b16c-856c75762765" />





The **OLED I²C lines** required careful attention. I kept the `SDA` and `SCL` traces under 100 mil length, and routed them directly from the Pro Micro’s pins to the display pads without detours. I placed the 10 kΩ pull‑up resistors right next to the Pro Micro pads to minimize stub length. A pair of bypass capacitors sat close to the OLED’s VCC and GND pads.



For the **rotary encoders**, each encoder had three nets: `ENC_A#`, `ENC_B#`, and `ENC_SW#`. I routed these from the encoders back to the Pro Micro GPIO pins using 8 mil traces. I added debounce capacitors (10 nF) and 10 kΩ pull‑up resistors right beside the Pro Micro footprint, shading them in a small component cluster for neatness.

### Fine‑Tuning and Finalizing

By late afternoon, I paused for lunch and realized I had spent nearly six hours just on routing. My eyes stung from staring at the screen, but the board was starting to look cohesive. I added four 3 mm mounting holes near the corners, mapped to screw posts I’d model in the case. I double‑checked the clearances for the keycap travel—making sure each cap could swing freely without hitting the enclosure walls.

Next, I generated a **3D preview** within EasyEDA. The black solder mask and white silkscreen contrasted nicely, and the placement of “CAT BOARD” above the OLED cutout looked bold and clear. I dragged and dropped the logo image onto the silk layer, traced its outline as vector lines, and deleted the raster image—now it was part of the board art.

At 8 PM, after exactly 8.5 hours of placement, routing, and endless tweaks, I exported the Gerber files and uploaded them to a local folder. My PC pinged with a message: “Gerber generation complete.” I leaned back, cracked a grin, and whispered to myself, “Mission accomplished—at least for today’s layout.”




<img width="955" height="464" alt="Screenshot 2025-07-13 161004" src="https://github.com/user-attachments/assets/49c8feac-f632-4616-ac21-aa79bfadabf0" />






---

## July 15 – BOM Finalisation,  & Case Modelling (4.5 hours)

Day 3 began with excitement and a to‑do list longer than my shopping cart. I had to finalize the BOM, configure QMK firmware, and prepare the case design in Fusion 360.

### BOM Compilation

I created a spreadsheet with columns for Component, Source, Part Number, Qty, Cost (INR), and Cost (USD). First on the list were **Gateron Clear mechanical switches**—sixty‑one for that silky smooth linear action. I found a 70‑pack on Amazon.in for ₹2,300, and adjusted the per‑switch cost to ₹2,300 ÷ 70 × 61 ≈ ₹2,005. Next were **PBT keycaps**—a charcoal grey set from neomacro.in priced at ₹2,550. Then the **Kailh hot‑swap sockets**, ₹1,275 for sixty‑one. Two **EC11 rotary encoders** at ₹170 each, two metal **encoder knobs** at ₹85 each, one **Pro Micro clone** for ₹850, one **0.91″ OLED module** for ₹600, a tube of **1N4148 diodes** for ₹85, **10 kΩ resistor pack** for ₹120, **10 nF caps** for ₹150, and **M2 screws and standoffs** for ₹200. I also added ₹425 for **JLCPCB shipping**, bringing the total BOM cost to about ₹8,740, comfortably under my ₹12,000 budget.


### Case Design in Fusion 360

I launched Fusion 360 for the enclosure. Starting with a rectangular plate matching the PCB dimensions (295 × 100 × 1.6 mm), I added four internal posts for M2 screws, positioned at the mounting holes. Then I extruded side walls 12 mm high and filleted the edges with a 2 mm radius for a smooth look. On the top plate, I cut out slots for the keycaps—each slot was 15 × 15 mm, spaced exactly to match the PCB footprints. I carved a 13 × 7 mm window for the OLED, and circular cutouts for the encoder shafts with 6 mm diameter. I also added a rectangular cutout for the USB‑C port on the front edge.





<img width="1073" height="746" alt="Screenshot 2025-07-13 160958" src="https://github.com/user-attachments/assets/3b0c575a-4e23-4e61-ac99-4afd79ee7ac6" />



<img width="995" height="867" alt="Screenshot 2025-07-13 161059" src="https://github.com/user-attachments/assets/98bdb03c-1c52-4c08-b5ad-6ccf8d229f82" />


<img width="744" height="623" alt="Screenshot 2025-07-13 163234" src="https://github.com/user-attachments/assets/65708f06-eeb9-42ff-9a29-236ef466c3fb" />


<img width="1103" height="657" alt="Screenshot 2025-07-13 163636" src="https://github.com/user-attachments/assets/64101145-60f7-4bb1-b5cd-f607e30a4c4f" />

<img width="900" height="450" alt="Screenshot 2025-07-13 172046" src="https://github.com/user-attachments/assets/d799ac07-3589-4b2e-8881-ce99f37a4196" />


To ensure proper clearance, I imported a simplified STEP model of my Pro Micro clone and used the “Joint” tool to place it exactly where it would sit on the PCB. Then I offset the case layers by 1 mm to account for solder joints and hot‑swap socket height. Finally, I exported two STL files (top and bottom) and arranged them on my Ender 3 bed layout, previewing print times: about 4 hours each at 0.2 mm layer height.




<img width="711" height="452" alt="Screenshot 2025-07-13 172055" src="https://github.com/user-attachments/assets/28cb8b1d-e7f4-4957-92d6-7a7653b00a4b" />



<img width="734" height="478" alt="Screenshot 2025-07-13 172113" src="https://github.com/user-attachments/assets/b7dda099-c340-467a-b52b-b30523b581da" />

<img width="733" height="490" alt="Screenshot 2025-07-13 172104" src="https://github.com/user-attachments/assets/f68f8dc1-f6ca-45f7-ad2b-e1a5e14bc06c" />



---



