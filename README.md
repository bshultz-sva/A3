# A3
assignment 3
Here are fourteen lines of code from my Escher staircase design (760 - 774). It takes the results of the build and turns them into the human-readable status message shown in the GUI.
Line by line: total_flights pulls out how many flights actually got built

seam computes the height of the "impossible" gap — how much higher the loop ends up than where it started, in Maya units, by multiplying total flights × steps per flight × riser height (the vertical rise per step). bridges is just how many bridges got built, which is always one fewer than the number of flights, since the very last flight is deliberately left unconnected to create the illusion.

if there's only one staircase, it formats a shorter message describing that single self-contained loop (flight count, step count, bridge count, seam height). Otherwise, it formats a longer message for the network mode, additionally reporting how many hubs and how many laps around them were completed, and it phrases the ending as "a visible gap" rather than just a height mismatch, since in network mode the loop doesn't close in the horizontal plane either.

        total_flights = self.build_result["total_flights"]
        seam = total_flights * steps_per_flight * riser_height
        bridges = max(0, total_flights - 1)
 
        if num_staircases == 1:
            label = ("Built 1 staircase: {0} flights x {1} steps, {2} bridge(s). "
                      "Vertical seam: {3:.2f} units (expected -- that's the illusion).").format(
                          total_flights, steps_per_flight, bridges, seam)
        else:
            label = ("Built a {0}-hub network: {1} lap(s), {2} flights x {3} steps, "
                      "{4} bridge(s) connecting hub to hub. Seam at closing hub: {5:.2f} "
                      "units + a visible gap (expected -- that's the illusion).").format(
                          num_staircases, self.build_result["laps"], total_flights,
                          steps_per_flight, bridges, seam)

 Either way, the resulting label string is what gets written into the status text field at the bottom of the tool window right after you click "Build Staircase(s)"



 One line I changed by hand was delete line 571 - "build" create camera line. I wanted to see the stairs on their own and felt this addition was not necessary.
