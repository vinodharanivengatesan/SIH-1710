
# SMART INDIA HACKATHON WORKSHOP

## NAME : vinodharani v
## REGISTER NUMBER : 212225040491
## DATE : 26/10/2026

## PROBLEM STATEMENT :
SIH 1710: Enhancing Navigation for Railway Station Facilities and Locations

## PROBLEM DESCRIPTION :
Background: Railway stations are complex environments with numerous facilities and locations such as ticket counters, platforms, restrooms, food courts, and waiting areas. Passengers often face difficulties in navigating these spaces, especially in large or unfamiliar stations. Efficient and user-friendly navigation systems are crucial for improving passenger experience, reducing congestion, and ensuring timely travel connections. Description: The problem involves developing a comprehensive navigation solution for railway stations that assists passengers in locating various facilities and destinations within the station premises. This includes creating detailed maps, providing real-time directions, and integrating features such as accessibility options for individuals with disabilities. The solution should be intuitive, easy to use, and accessible via multiple platforms, including mobile devices and digital kiosks. Key challenges include updating navigation information in real-time, ensuring accuracy, and accommodating the diverse needs of all passengers. Expected Solution: The expected solution is a multi-platform navigation system that provides detailed, real-time directions to all facilities and locations within a railway station. This system should include: A mobile application with 3D interactive maps and step-by-step navigation. Digital kiosks located throughout the station with touch-screen interfaces. Voice-guided navigation for visually impaired passengers. Regular updates to reflect changes in station layout and facility locations. Integration with existing railway apps and services for seamless user experience. The solution should enhance the overall passenger experience by reducing confusion, saving time, and improving accessibility within the station.

## PROBLEM CREATER'S ORGANISATION :
Ministry of Railway

## IDEA :
RailPath is a digital-twin-based station navigator that shows passengers the best route right now, not just the shortest path. It combines four things:

- **Train awareness:** the passenger enters a PNR or train number, and the app guides them to the platform and their coach position, with a “Time-to-Board” countdown.
- **Crowd awareness:** routes avoid congested gates and footbridges using count-only data from CCTV and Wi-Fi/BLE signals.
- **Personal needs:** wheelchair, elderly, heavy luggage, family with kids, and visually impaired profiles each get suitable routes (ramps, lifts, tactile paths).
- **Live updates:** platform changes, lift outages, and closures reroute every affected user instantly.

## PROPOSED SOLUTION / ARCHITECTURE DIAGRAM :

### Layers

1. **User interfaces:** mobile app, PWA opened via QR code, kiosk UI, voice and haptic interface
2. **API gateway:** authentication, rate limiting, language routing
3. **Core services:**
   - Routing Engine: A*/Dijkstra with edge cost = distance + crowd penalty + accessibility penalty + time-pressure factor
   - Positioning Service: BLE + Wi-Fi + pedestrian dead reckoning + QR anchors
   - Crowd Analytics Service: edge-based people counting per zone
   - Train Info Service: NTES/IRCTC feeds for status, platform, and coach position
4. **Digital twin data layer:** station graph, POI database, live status cache, event stream
5. **Station admin console:** map editor, closures, lift status, announcements, heatmaps, audit logs

![RailPath Architecture Diagram](https://github.com/user-attachments/assets/231af888-46e4-4655-b0e3-3d59aac65eb5)

## USE CASES :

1. **First-time traveller:** enters a PNR and is guided from the entrance to the platform and coach position.
2. **Wheelchair user:** gets a ramp- and lift-only route with live lift status.
3. **Visually impaired passenger:** receives voice and haptic turn-by-turn guidance to the restroom, with an assistance button.
4. **Late passenger:** “Fast mode” gives the quickest route and warns if boarding is risky.
5. **Platform change:** the user gets an instant alert and an automatic reroute.
6. **Elderly passenger with luggage:** is routed via lifts or battery car, with an option to book a porter.
7. **Festival rush:** alternate gates are suggested and crowd heat is shown.
8. **Emergency:** evacuation routes avoid blocked and crowded zones.
9. **Station staff:** mark a lift as out of service, and routes update everywhere instantly.
10. **Non-app user:** scans a QR code on a kiosk or signboard and uses the web app.
11. **Railway authorities:** use heatmaps and dwell-time analytics to improve layout and signage.

## TECHNOLOGY STACK:

![RailPath Technology Stack](https://github.com/user-attachments/assets/fb5e7e3f-0106-4579-80d7-ba1366610bac)

## DEPENDENCIES :

### Data

1. Station floor plans (CAD/PDF/BIM) from the railway authority
2. Live train data feeds (NTES, IRCTC) for status, platform, and coach position
3. Facility inventory (lifts, escalators, restrooms, food stalls)

### Hardware

1. BLE beacons (roughly one per 10-15 m in key zones)
2. CCTV cameras with edge compute devices
3. Weatherproof, accessible touch-screen kiosks
4. Station Wi-Fi infrastructure
5. Tactile paving (mapped where available)
