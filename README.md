I had been typing away on my old membrane board for months, and every keystroke felt flat and uninspired. One evening, while sipping chai and scrolling through keyboard community photos, I thought, yaar, I need something that’s truly mine. That’s when the idea for Neon Beats struck me. I sketched out a classic 65 percent layout in my notebook, then shifted to EasyEDA where I placed sixty‑one hot‑swap switch footprints and two rotary encoders at the top right. But I wanted one more thing to make it stand out: a little 0.91‑inch OLED screen tucked between the encoders so I could see which layer I’m on, check a quick timer, or even show a simple logo when the board is idle.




<img width="900" height="450" alt="Screenshot 2025-07-13 172046" src="https://github.com/user-attachments/assets/68eeb1da-c812-4b62-8edd-483474c7050b" />


<img width="1022" height="510" alt="Screenshot 2025-07-13 161436" src="https://github.com/user-attachments/assets/4382b79c-2881-44ec-a37a-05a92fc481ae" />





Once the PCB design was squared away, I sent five copies to JLCPCB with a black solder mask and crisp white silkscreen reading Neon Beats. To save costs and embrace a little desi jugaad, I skipped the full PCBA option and instead hand‑soldered the Pro Micro and the SMD diodes myself. That late‑night soldering session under my desk lamp was oddly therapeutic, each tiny diode click‑click into place giving me a deeper connection with the board. When I first powered it up, seeing the OLED light up with a welcome graphic was pure satisfaction.



<img width="1042" height="467" alt="Screenshot 2025-07-13 154307" src="https://github.com/user-attachments/assets/078b064f-30e1-4858-baf1-baee8d8cdbad" />




<img width="975" height="621" alt="Screenshot 2025-07-13 190219" src="https://github.com/user-attachments/assets/e9ad6d3e-b87d-45dc-be41-e708dea4240e" />




<img width="955" height="464" alt="Screenshot 2025-07-13 161004" src="https://github.com/user-attachments/assets/123ed4f9-3977-4105-8bbd-4f79b9a201a0" />



For the case I switched to Fusion 360, modelling a sleek, low‑profile shell with curved edges that would grip the PCB just right. I printed it on my Ender 3 in matte black PLA, and the finish looked mast. The fit was snug and the matte texture matched the black PCB perfectly. I even carved out a small recess for the OLED screen so its glow softly diffuses through the front panel. Next to it, the two rotary knobs give precise control for volume and media playback, and I can twist or press them for fast actions.





<img width="1103" height="657" alt="Screenshot 2025-07-13 163636" src="https://github.com/user-attachments/assets/4d8330ad-1c4e-4911-a309-d08699ca50d1" />




<img width="914" height="518" alt="Screenshot 2025-07-13 170030" src="https://github.com/user-attachments/assets/1c5a799a-d5ba-42c9-a312-6474da50bb41" />



<img width="744" height="623" alt="Screenshot 2025-07-13 163234" src="https://github.com/user-attachments/assets/b8110a95-d89d-4341-ba96-591a50700bae" />






Populating the board was one of the most fun evenings I’ve had in a while. I pressed Gateron Yellow switches into Kailh hot‑swap sockets, each one clicking satisfyingly as it seated. The PBT dye‑sublimated keycaps in jet black snapped on firmly, legends so crisp that I know they will never fade. After wiring the OLED via I²C to the Pro Micro, I double‑checked connections, plugged in the USB‑C cable, and watched the little screen come to life. I had QMK configured to show the current layer in big text, a small animation when the board is idle, and even a typing speed counter if I hold the function key. It’s simple but feels high‑end.


https://github.com/user-attachments/assets/973e51d9-64d8-481f-b7a6-e098c4fb3048














Building Neon Beats taught me that elegance and functionality don’t need flashy RGB floodlights. This keyboard is about pure mechanical satisfaction, a reliable Pro Micro brain, and a little OLED to keep me informed. It’s a perfect blend of desi jugaad spirit and modern maker culture, and every time I sit down to type, I feel proud of what I’ve created.




<img width="1096" height="667" alt="Screenshot 2025-07-13 161454" src="https://github.com/user-attachments/assets/4d757906-a59d-4ac0-979a-6489f271dbe5" />





<img width="995" height="867" alt="Screenshot 2025-07-13 161059" src="https://github.com/user-attachments/assets/36675704-77d4-41b7-bbb5-1da27e4cb669" />











Here is the streamlined Bill of Materials in Indian rupees and US dollars, keeping the total under $140:

Component	Source & Link	Qty	Total Cost (INR)	Total Cost (USD)
Gateron Yellow Mechanical Switches	Amazon.in (70‑pack)	61	₹2,400	$25
PBT Dye‑sublimated Keycaps (Black)	neomacro.in	61	₹2,550	$30
Kailh Hot‑swap Sockets	neomacro.in	61	₹1,275	$15
Rotary Encoders	neomacro.in	2	₹340	$4
Encoder Knobs	neomacro.in	2	₹170	$2
0.91″ OLED Screen Module	Amazon.in	1	₹600	$8
Custom PCB (5 pcs)	JLCPCB via EasyEDA	5	₹2,550	$30
Arduino Pro Micro	Amazon.in	1	₹850	$10
Diode Kit (100 pcs, 1N4148)	Amazon.in	1	₹85	$1
Shipping (PCBs)	JLCPCB	1	₹425	$5
PLA Filament (Matte Black)	Local Supplier	–	₹800	$10

Total cost for Neon Beats comes to approximately ₹11,645 or about $130, leaving room for any small extras while keeping the build under $140. Neon Beats now sits proudly on my desk, every keystroke a reminder of late‑night soldering, Fusion 360 tweaks, and the simple joy of making something truly my own.
































