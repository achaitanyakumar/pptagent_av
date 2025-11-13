# AR-Based Indoor and Outdoor Campus Navigation System using Unity and ARCore

# Abstract

This paper demonstrates a mobile Augmented Reality (AR) navigation system for enhancing campus tour experiences with immersive, interactive, and real-time spatial information. The system utilizes Unity and ARCore, relying on the camera and sensor features of contemporary smartphones.

For indoor navigation, the app utilizes marker-based tracking with image targets located at strategic intersections. These markers activate AR content like direction arrows and animated routes via Unity's LineRenderer that push users towards their destination in buildings.

For out-of-doors navigation, the system combines GPS with compass orientation to position world-anchored AR markers in alignment with actual world geolocations. It leads users along campus through real-time location-aware 3D visual instructions. Also, interactive AR areas display 3D models of important landmarks with contextual and cultural data on the surrounding campus environment.

The app enables dynamic location choice through dropdown menus and visual overlays of paths to improve user experience. The project was tested on several Android devices that support ARCore and showed high accuracy in marker detection, adaptive outdoor pathfinding, and overall user satisfaction. The findings indicate enhancements in navigation accuracy, less confusion in intricate areas, and enhanced user engagement.

This system fills the gap in between indoor and outdoor navigation and provides a scalable AR platform for schools, museums, and public buildings.

# 1. Introduction

Wayfinding across extensive educational campuses can prove to be a daunting task for visitors, students, and lecturers alike. It becomes more difficult with multi-building campuses, more than one floor, and no interactive directions. Although conventional methods like static maps, signboards, and printed brochures are used frequently, they prove lacking, particularly in indoor spaces where GPS signals do not reach or are very weak.

Outdoor navigation has already been dealt with commercially by solutions such as Google Maps; however, such solutions do not normally cater to indoor localization, are not integrated with indoor maps, and offer no contextual or immersive instructions. Indoor AR navigation is in a nascent stage, with current systems often reliant on costly infrastructure such as beacons or Wi-Fi fingerprinting and hence not suited for large-scale deployment.

In order to fulfill this need, this paper introduces a consolidated Augmented Reality (AR) navigation system for both indoor and outdoor use through a smartphone application developed with Unity and Google ARCore. The system employs marker-based tracking to navigate indoors, enabling the app to identify designated visual targets (e.g., advertisements or indicators) and show navigational hints on the AR screen. In outdoor navigation, the system combines GPS and compass information to set AR markers at real-world coordinates and direct users to their destination.

Aside from rudimentary navigation, the system incorporates interactive AR spaces that render 3D models and informative content regarding significant locations, thus enhancing campus interaction. The integration of Unity's rendering performance and ARCore's tracking solutions allows for a lightweight, accessible, and scalable solution for academic campuses, museums, and public facilities.

This paper documents the design, implementation, and analysis of the system and examines its applications, limitations, and future enhancement.

# 2. Related Work

There have been various proposals for indoor and outdoor navigation with Augmented Reality (AR), but they mostly come with either the need for extra hardware or limited accuracy and scalability.

# 2.1 Indoor Navigation Methods

Indoor navigation has widely been researched with technologies such as:

QR Codes: Low cost and simple to deploy, but poor on visual appeal and live interaction.

BLE Beacons: Need special hardware installation, prone to signal drift and expensive maintenance.

Wi-Fi Fingerprinting: Requires signal mapping and calibration, which isn't scalable to dynamic indoor configurations.

Marker-based tracking through SDKs such as Vuforia and Immersal has proven to be a viable alternative. Though Vuforia provides robust image recognition, its licensing may be limited. Immersal, a spatial mapping specialist, is strong but severely limited within its free plan, including:

● Only 100 image uploads permitted. It also involves scanning a medium-sized space that usually takes 50–60 images, which quickly depletes the free limit.

# 2.2 Navigation Strategies for Outdoor

Outdoor AR outdoor navigation has been piloted on tourism and city guide apps. They usually depend on GPS and compass support, but present difficulties such as:

● Real-time alignment errors ● Compass discrepancies dependent on devices ● Rendering geospatial content latency

# 2.3 SDKs and Tools Explored

Several SDKs and tools were analyzed for this project. Each had its advantages and limitations:

<table><tr><td rowspan=1 colspan=1>SDK / Tool</td><td rowspan=1 colspan=1>Observations</td></tr><tr><td rowspan=1 colspan=1>ImmersalSDK</td><td rowspan=1 colspan=1>Good for room-scale mapping, but limited free image quota (100);scanning a room needs ~60 images.</td></tr><tr><td rowspan=1 colspan=1> StardustSDK</td><td rowspan=1 colspan=1> No longer available -“Temporarily offline due to strategicreorganisation&quot; (source: Neogoma official YouTube).</td></tr><tr><td rowspan=1 colspan=1>ZapWorks +Mattercraft</td><td rowspan=1 colspan=1>Web-based, works on Android and iOs,but becomes paid after Jan31st. Suitable for light AR experiences.</td></tr><tr><td rowspan=1 colspan=1>GoogleGeospatialCreator</td><td rowspan=1 colspan=1>Offers excellent outdoor AR anchoring, but requires API access viacredit card.</td></tr><tr><td rowspan=1 colspan=1>Matterport/ Mapbox</td><td rowspan=1 colspan=1> Enterprise-grade but entirely paid; not ideal for small educationaluse cases.</td></tr><tr><td rowspan=1 colspan=1>NianticLightshipVPS</td><td rowspan=1 colspan=1>Provides 3D anchors and real-world scanning, but compatibility issues exist between Unity and Android versions. Frequent errors like GUID failure, making it unstable for production use.</td></tr></table>

# 2.4 Conclusion

In contrast to available systems that concentrate on either indoor or outdoor spaces and usually need specialized SDKs or hardware, our method:

● Marries image-target-based indoor navigation with GPS-powered outdoor navigation.   
● Evades third-party SDK restrictions through Unity $^ +$ ARCore, which is free as well as mobile-native.   
● Offers end-to-end navigation without the use of external beacons, Wi-Fi mapping, or paid APIs.

# 3. System Design and Architecture

# 3.1 Tools and Technologies

- Unity: Core engine for 3D rendering and logic - ARCore: Handles AR tracking and camera feed - C#: Backend scripting - Blender: Custom 3D model creation - $\mathbf { G P S + }$ Compass: Outdoor location orientation - LineRenderer: Visual path guidance

# 3.2 Indoor Navigation Flow

Indoor navigation is done through image targets strategically positioned at points such as doorways and corridors. Upon scanning these markers by a user, Unity (through ARCore) identifies the image and shows a floating path with the LineRenderer component.

The following custom NavigationTarget script takes care of:

● Dynamic change of the path depending on the user-chosen destination.   
$\bullet$ Enabling the right path segment within the AR scene. Enabling rapid re-scanning to reset view or re-orient.

This strategy obviates the requirement for GPS or Wi-Fi in indoor settings and provides continuous AR direction with unobstructed visual routes.

# 3.3 Outdoor Navigation Flow

When in outdoor mode, the app utilizes the device's compass and GPS to find the user's position and orientation. Depending on the destination chosen, the system positions AR markers in world space, aligned with real-world coordinates.

Similar to indoor navigation, a LineRenderer is utilized for rendering a floating line from the user's position to the destination. The line is updated in real time as the user walks, offering precise visual direction across campus spaces without physical signs.

# 4. Features Implemented

- Indoor Pathfinding: Room-to-room directional path in AR with markers - Outdoor Wayfinding: Real-world navigation with AR markers and compass - AR Cultural Zones: Interactive 3D models presented in important cultural locations - Re-centering with Markers: Guarantees precision using adjacent posters or image targets - UI Controls: Location selection dropdown and path view toggle

# 5. Experimental Results

# 5.1 Test Environment

Campus area: ${ \sim } 2 0 { , } 0 0 0$ sq. ft. Devices used: Pixel 6, Samsung Galaxy A52 (ARCore-supported) Indoor markers: Printed posters with high-contrast images

# 5.2 Performance Metrics

Indoor Detection Accuracy: ${ \sim } 9 0 \%$   
Outdoor GPS Accuracy: ${ \sim } 2 0$ to 40 meters average error   
Frame Rate (avg.): 30-40 FPS   
App Size: ${ \sim } 2 5 0$ MB   
Usability Feedback (10 users): Avg. 8.5/10

# 6. Limitations and Future Scope

# 6.1 Limitations

- GPS lags in dense buildings - Marker visibility depends on lighting - Real-time map anchoring not available in low-end devices

# 6.2 Future Enhancements

- Replace markers with spatial anchors using Immersal SDK/Vuforia SDK   
- Add multi-floor indoor navigation   
- Integrate speech-based assistant   
- Web-based admin panel for managing paths and 3D content

# 7. Conclusion

The proposed AR-based navigation system significantly improves user experience during campus tours. It enables seamless switching between indoor and outdoor environments with accurate and engaging guidance. The project demonstrates the potential of AR to

enhance wayfinding in real-world settings and can be extended to other use cases like malls, hospitals, and museums.

# 8. References

1. ARCore Developer Guide – https://developers.google.com/ar   
2. Unity Documentation – https://docs.unity3d.com   
3. Vuforia Engine – https://developer.vuforia.com   
4. Immersal SDK – https://immersal.com   
5. Indoor Navigation using AR – IEEE Xplore   
6. “ARKit and ARCore Comparison” – ACM XR Survey, 2022