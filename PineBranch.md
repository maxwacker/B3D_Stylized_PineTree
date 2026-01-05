# Pine Branch From RK 
https://www.youtube.com/watch?v=qBKtjZQY7r0
    
## 01:20 Cube start
    scale .15, Apply Scale
    
    Edit Mode
    scale X .05
    scale Z to get needle size

## 02:00 Shape it
    Scale down top
    Add 2 loop cut
    Grab up the middle part to give curvature
    
## 02:30 Smooth it
    Object mode
    CTRL 1 (SubDiv)
    Shade smooth
    
    Back to Edit mode 
    Add loop cut near top to sharpen the very end
    Do the same on bottom
    
## 03:00 Branch from Curve
    Object mode add Bezier curve
    Edit Mode, rotate handles to be up/down, 1st handle at world origin
    
## 03:20 GN
    Object Mode, new GN
    
    Give Thickness with : CurToMesh, CurveCircle as profile
    
## 04:30 Control Radius
    Add SetCurveRadius, before CurveToMesh
    <Blender 4.5 - Fix SetCurveRadius: https://projects.blender.org/blender/blender/issues/149611>
    
## 04:55
    Adjust radius along curve
    Put (new) SplineParam.Factor into SetCurveRadius.Radius
    
    <>
    Replacing ColorRamp Control for Radius
    by Spline Handle indiviual scaling control
    from https://www.youtube.com/watch?v=YMwzdcMkado
    </>
    
    Frame the radius GNs with name
    
## 06:30 Instanciate needles
    Add InstanceOnPoint Setup
    Use ObjectInfo(Needle) as Instance input
    Join with main (branch) geometry
    
## 07:45 Control needle instances scattering
    Add ResampleCurve node
    Notice issue: that instance spacing depends on Curve length
    Fix: Change Resample Mode from Count To Length
    Set Length param value to O.OO24 
    (Seems to make too mush needles,but will be fix by random roatation later)
    
    Notice issue: Rotating Curve handle doesn't lead to reorient needles accordingly
    Fix : ...
    
## 09:10 Aglin Needle perpendicularmy to (main) branch
    Add AlignRotationToVector Node with CurveTangeant as Vector input
    This fixex last issue (make needle perpendicular to branch)
    
## 09:55 Randomize needle scale
    Add RandomValue .6-1.0 to InstanceOnPoints.Scale
    Frame the whole instancing nodes into dedicated Frame 'NeedlesOnCurve'

## 10:35 Rotateneedeles around branch
    Add RotatateInstances after InstancesOnPoints
    Put a RandomValue Vector into the Rotation 
    Random.Max : 0.0, 0,0, tau (2*pi)
    
    Looking at real (natural) branch spawn, notice they are point up in main branch direction
    Fix : X.min = -.05 X.Max = -1.0
    
    Frame these 2 last into "Needles roation" 

## 12:40 Material
    Add Mat, Don't forget to SetMAtaerial in GN (for main branch only, before join)
    Add a Noise Texture Scale at 80.0 and Detail at 10 with TextCoords input.Object input Vector
    
    Use Noise.Factor for 2 constante (brown) ColorMix
    And also as Bump.Height -> Normal. Strength 0.3, Distance 1.0
    
    Set PBSDF.Roughness to 0.7
    
## 14:50 Needle Mat
    New MAt (on SetMat on GN)
    Roughness 0.6
    Since this organic material, set some transmission Weight : 0.6
     
## 15:00 Lgthing
    