##Cabinet
Looking to build your own full-size Devcade? You’ve come to the right place! This document contains all the information about the construction of the current Devcade cabinet, and includes the files you need to create your own. Of course, it doesn’t have to be 1:1, so have some fun with it. 

Something to keep in mind, I (DeadPixelPro) was the creator of this design. The thing is, I’m a web developer, not an…. Arcade cabinet designer person. So, if you have any suggestions for improvements to make to the design, we would love to hear them.

The cabinet was primarily designed in Cinema4D, with minor adjustments made in Adobe Illustrator. 

##Exterior
For the panels, we used three 4x8ft sheets of Sande Plywood, 3/4ths of an inch thick. Most traditional arcade cabinets use MDF, but we opted for Sande Plywood for its durability. MDF is certainly cheaper though, so if you’re not planning on placing your cabinet in a public space, or aren’t planning to move it around much, we would recommend looking into MDF. We cut the sheets using an automated cnc router, with the attached DXF files. If you don’t have access to a machine like this, we’d recommend using a handheld router for the side panels, and a table saw for the other panels. 

For securing the panels together, we opted to use T-Nuts in the side panels, with L-brackets secured directly to the other panels. We used T-Nuts since we wanted to be able to disassemble the cabinet for travel, though this significantly increased the cost. If you don’t plan to move it around much, you could opt to secure the panels with simple brackets and screws. If you do this, we’d recommend you route the slots for the T-molding first. The side panels also include cleats, though these aren’t depicted in the documentation.

The rear door is held in with cleats and a standard cabinet lock.

We used acrylic for the monitor bezel and the marquee, cut with a laser (though a tablesaw with a specfic blade and disabed sawsstop mechanism would suffice). We used a sheet 24x48 inches in size, 1/4ths of an inch thick.

Routing the T-molding for the side panels can be done with a handheld router with a slot cutter.

The current arcade control panel is made of wood, though we’re intending to replace this later on with a panel made with a 16 gauge steel sheet. This sheet will also be used to cut brackets that hold in the marquee and the monitor cover.

The monitor is held in using a horizontally-mounted plywood piece, and a flat monitor mount. Placement of this piece will depend on the mount and monitor used, and will need to be measured.

##Electronics
Devcade's most notable feature is its portrait 9:16 4K display. We went with a 32" 4k 60Hz Samsung display. You don't need this exact size, though the software currenty assumes a 4k 60Hz display will be present, so we can't currently guarantee other resolutions and refresh rates will play nice. Remember to select a monitor with relatively low latency.

The speakers are standard 5.25" coaxial speakers. If you use a different size, remember to grab correctly sized speaker grills, and adjust the size of the speaker holes. They're powered by a generic AMP with 18W per channel.

We used an LED light bar for the maruqee for their long life and power efficiency.

The control panel is a Pi Pico set to act as two different gamepads. For more info about the control panel specifically, check the Gamepad section.
