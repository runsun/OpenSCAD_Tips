## OpenSCAD snippets for copy and paste ##



| Type | API | Source | Remark |
|------|-----|--------|--------|
|Func| **hash**( *h,k* ) | Runsun | Very efficient search()-based associated array|

```javascript
function hash(h,k, notfound)= 
(
  let(rtn = h[ search([k], [for(i=[0:2:len(h)-2])h[i]])[0]*2+1 ])
  rtn==undef?notfound:rtn
);  

echo( hash( ["a",1,"b",2], "a" ) );  // 1
echo( hash( ["a",1,"b",2], "b" ) );  // 2
echo( hash( ["a",1,"b",2], "c" ) );  // undef
echo( hash( ["a",1,"b",2], "c", "missing" ) ); // "missing"
```

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Module| **Line**( *pts* ) | Inspired by [Ronaldo](http://forum.openscad.org/Can-you-sweep-a-object-with-fingers-tp19057p19330.html) | Much more efficient than a direct hull() of points|

```javascript
module Line( pts, r=0.05, closed=false, color=undef, transp=1, fn=4 )
{
  if(len(pts)>1 && len(pts[0])>1 && r>0) 
  { 
    // Convert to 3d if 2d; Attach 1st pt if closed
    pts  = concat( [for(p=pts) [ p[0],p[1],p[2]==undef?0:p[1] ]],  
                  closed? [[ pts[0][0], pts[0][1], pts[0][2]==undef?0:pts[0][2] ]] : []
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
