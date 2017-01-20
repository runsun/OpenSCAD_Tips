## OpenSCAD snippets for copy and paste ##


| Type | API | Source | Remark |
|------|-----|--------|--------|
|Module| **Line**( *pts, [r,closed,color,transp,fn]* ) | Inspired by [Ronaldo](http://forum.openscad.org/Can-you-sweep-a-object-with-fingers-tp19057p19330.html) | |

```javascript
module Line(pts, r=0.05, closed=false, color=undef, transp=1, fn=4)
{
  if(len(pts)>1 && len(pts[0])>1 && r>0) 
  { 
    // Convert to 3d if 2d; Attach 1st pt if closed
    pts  = concat( [for(p=pts) [ p[0],p[1],p[2]==undef?0:p[1] ], 
                  closed? [ [pts[0][0], pts[0][1], pts[0][2]==undef?0:pts[0][2] ] : []
                 ); 
    color(color,transp)
    for(i=[0:len(pts)-2]) 
    { 
       v = pts[i+1]-pts[i]; 
       L = norm(v); 
       if( L > 1e-12) 
         translate(pts[i]) 
         rotate([0, acos(v[2]/L), atan2(v[1],v[0])]) 
         rotate(45) cylinder(h=L, r=r, $fn=fn); 
    } 
  } 
}     
```
