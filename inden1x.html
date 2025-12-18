<!DOCTYPE html>
<html>
  <head>
    <title>VR Optical Bench Simulation</title>
    <meta name="description" content="Interactive VR Optical Bench">
    <script src="https://aframe.io/releases/1.4.0/aframe.min.js"></script>
    <script src="https://unpkg.com/aframe-environment-component@1.3.2/dist/aframe-environment-component.min.js"></script>
    
    <!-- FONT FOR TEXT -->
    <script src="https://unpkg.com/aframe-troika-text/dist/aframe-troika-text.min.js"></script>
  </head>
  <body>

    <!-- JAVASCRIPT LOGIC -->
    <script>
      // COMPONENT: Handle Button Clicks to Move Lenses
      AFRAME.registerComponent('lens-control', {
        schema: {
          target: {type: 'selector'},
          direction: {type: 'number', default: 1} // 1 for forward, -1 for backward
        },
        init: function () {
          this.el.addEventListener('click', () => {
            let pos = this.data.target.getAttribute('position');
            // Limit movement range so it stays on the table
            let newZ = pos.z + (0.2 * this.data.direction);
            
            // Constrain movement (Rail is roughly from -1 to -5)
            if(newZ < -1 && newZ > -5.5) {
                this.data.target.setAttribute('position', {x: pos.x, y: pos.y, z: newZ});
            }
          });
          
          // Hover visual effect
          this.el.addEventListener('mouseenter', () => { this.el.setAttribute('color', '#4CC3D9'); });
          this.el.addEventListener('mouseleave', () => { this.el.setAttribute('color', '#222'); });
        }
      });

      // COMPONENT: Real-time Ray Tracing & Data Display
      AFRAME.registerComponent('ray-tracer', {
        tick: function () {
          const source = document.querySelector('#light-source');
          const lens1 = document.querySelector('#lens-1-group');
          const lens2 = document.querySelector('#lens-2-group');
          const screen = document.querySelector('#screen-group');
          const beams = document.querySelector('#beams');
          const readout = document.querySelector('#readout-text');

          // Get World Positions
          const p0 = new THREE.Vector3();
          const p1 = new THREE.Vector3();
          const p2 = new THREE.Vector3();
          const p3 = new THREE.Vector3();

          source.object3D.getWorldPosition(p0);
          lens1.object3D.getWorldPosition(p1);
          lens2.object3D.getWorldPosition(p2);
          screen.object3D.getWorldPosition(p3);

          // Update Laser Lines
          // Segment 1: Source -> Lens 1
          beams.setAttribute('line', `start: ${p0.x} ${p0.y} ${p0.z}; end: ${p1.x} ${p1.y} ${p1.z}; color: red; opacity: 0.8`);
          
          // Segment 2: Lens 1 -> Lens 2
          beams.setAttribute('line__2', `start: ${p1.x} ${p1.y} ${p1.z}; end: ${p2.x} ${p2.y} ${p2.z}; color: red; opacity: 0.8`);
          
          // Segment 3: Lens 2 -> Screen
          beams.setAttribute('line__3', `start: ${p2.x} ${p2.y} ${p2.z}; end: ${p3.x} ${p3.y} ${p3.z}; color: red; opacity: 0.8`);

          // Calculate Distances for Data Panel
          let d1 = p0.distanceTo(p1).toFixed(2);
          let d2 = p1.distanceTo(p2).toFixed(2);
          
          readout.setAttribute('value', 
            `DATA MONITOR\n\nSource to Lens 1: ${d1}m\nLens 1 to Lens 2: ${d2}m\n\nStatus: Active`);
        }
      });
    </script>

    <!-- SCENE START -->
    <a-scene ray-tracer cursor="rayOrigin: mouse" raycaster="objects: .clickable">
      
      <!-- 1. ENVIRONMENT -->
      <a-entity environment="preset: starry; groundColor: #1a1a1a; grid: none"></a-entity>
      
      <!-- Lighting -->
      <a-light type="ambient" color="#444"></a-light>
      <a-light type="point" position="2 4 4" intensity="0.5"></a-light>

      <!-- 2. UI / INSTRUCTIONS -->
      <a-entity position="0 2.2 -3">
          <a-plane width="3.5" height="0.8" color="#000" opacity="0.7"></a-plane>
          <a-text value="OPTICAL BENCH SIMULATION\nClick the [ < ] and [ > ] buttons to move lenses.\nObserve the light path updating in real-time." 
                  align="center" color="white" width="4"></a-text>
      </a-entity>

      <!-- 3. THE BENCH SETUP -->
      <a-entity position="0 1 -3.5">
        
        <!-- The Rail (Table) -->
        <a-box width="0.4" height="0.05" depth="7" color="#333" metalness="0.6" position="0 -0.05 -1"></a-box>
        <!-- Ruler Markings -->
        <a-box width="0.05" height="0.06" depth="7" color="#fff" position="0 -0.05 -1"></a-box>

        <!-- A. LIGHT SOURCE (Stationary) -->
        <a-entity id="light-source" position="0 0.25 1.5">
            <a-box color="#222" depth="0.3" height="0.3" width="0.3"></a-box>
            <a-cylinder rotation="90 0 0" height="0.1" radius="0.05" color="red" position="0 0 -0.15"></a-cylinder>
            <a-text value="SOURCE" align="center" position="0 0.25 0" width="3"></a-text>
            <!-- Glowing effect -->
            <a-light type="point" color="red" distance="2" intensity="2"></a-light>
        </a-entity>

        <!-- B. LENS 1 (Movable) -->
        <a-entity id="lens-1-group" position="0 0.25 -0.5">
            <!-- The Glass -->
            <a-sphere scale="1 1 0.1" radius="0.35" color="#aaddff" opacity="0.4" metalness="0.9" roughness="0.1"></a-sphere>
            <a-ring radius-inner="0.34" radius-outer="0.38" color="#111"></a-ring>
            <!-- The Stand -->
            <a-cylinder height="0.4" radius="0.02" position="0 -0.4 0" color="#111"></a-cylinder>
            <a-text value="LENS 1" align="center" position="0 0.5 0" width="3"></a-text>
            
            <!-- Controls for Lens 1 -->
            <a-entity position="0.5 0 0">
                <a-plane class="clickable" lens-control="target: #lens-1-group; direction: 1" 
                         width="0.2" height="0.2" color="#222" position="0 0 0.15">
                     <a-text value="<" align="center"></a-text>
                </a-plane>
                <a-plane class="clickable" lens-control="target: #lens-1-group; direction: -1" 
                         width="0.2" height="0.2" color="#222" position="0 0 -0.15">
                     <a-text value=">" align="center"></a-text>
                </a-plane>
            </a-entity>
        </a-entity>

        <!-- C. LENS 2 (Movable) -->
        <a-entity id="lens-2-group" position="0 0.25 -2.5">
            <!-- The Glass -->
            <a-sphere scale="1 1 0.15" radius="0.45" color="#aaddff" opacity="0.4" metalness="0.9" roughness="0.1"></a-sphere>
            <a-ring radius-inner="0.44" radius-outer="0.48" color="#111"></a-ring>
            <!-- The Stand -->
            <a-cylinder height="0.4" radius="0.02" position="0 -0.4 0" color="#111"></a-cylinder>
            <a-text value="LENS 2" align="center" position="0 0.6 0" width="3"></a-text>

            <!-- Controls for Lens 2 -->
            <a-entity position="-0.5 0 0" rotation="0 180 0">
                <a-plane class="clickable" lens-control="target: #lens-2-group; direction: -1" 
                         width="0.2" height="0.2" color="#222" position="0 0 0.15">
                     <a-text value=">" align="center" rotation="0 180 0"></a-text>
                </a-plane>
                <a-plane class="clickable" lens-control="target: #lens-2-group; direction: 1" 
                         width="0.2" height="0.2" color="#222" position="0 0 -0.15">
                     <a-text value="<" align="center" rotation="0 180 0"></a-text>
                </a-plane>
            </a-entity>
        </a-entity>

        <!-- D. SCREEN (Stationary Target) -->
        <a-entity id="screen-group" position="0 0.25 -4.5">
            <a-box width="1" height="1" depth="0.05" color="#fff" opacity="0.9"></a-box>
            <a-cylinder height="0.75" radius="0.02" position="0 -0.4 0" color="#111"></a-cylinder>
            <a-text value="SCREEN" align="center" color="#333" position="0 0.6 0" width="3"></a-text>
        </a-entity>

        <!-- E. LASER BEAMS (Drawn by JS) -->
        <a-entity id="beams"></a-entity>

      </a-entity>

      <!-- DATA DASHBOARD -->
      <a-entity position="-2 1.5 -2" rotation="0 30 0">
        <a-plane width="1.5" height="1" color="#002200" opacity="0.9" metalness="0.5" border="color: #fff; width: 0.02">
            <a-text id="readout-text" 
                    value="Initializing..." 
                    align="center" width="1.3" color="#00ff00" font="sourcecodepro"></a-text>
        </a-plane>
      </a-entity>

      <!-- CAMERA RIG -->
      <a-entity position="0 1.6 0.5">
        <a-camera look-controls wasd-controls>
            <!-- Reticle for interacting (VR/Gaze) -->
            <a-cursor color="yellow" fuse="false"></a-cursor>
        </a-camera>
      </a-entity>

    </a-scene>
  </body>
</html>
