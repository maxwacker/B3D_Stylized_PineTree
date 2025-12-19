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
    