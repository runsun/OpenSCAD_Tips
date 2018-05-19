## OpenSCAD snippets for copy and paste ##

#### Menu
| [**hash**( *h,k* )](#hash) | [**ichar**( *s,c* )](#ichar) | [**Line**( *pts* )](#line) | [**rotate-fixed**](#rotate_fixed) | [**rotate-any dir**](#rotate_anydir) | [**rotate-any axis**](#rotate_anyaxis) | [**sortArrs**( *arrs,by=0* )](#sortarrs) |
|--|--|--|--|--|--|--|

---
### hash
| Type | API | Source | Remark |
|------|-----|--------|--------|
|Func| **hash**( *h,k* ) | Runsun | Very efficient search()-based associated array|

```c++
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


```c++
// Associated functions:

function keys(h)= [for(i=[0:2:len(h)-2]) h[i]];
function vals(h)= [for(i=[1:2:len(h)]) h[i]];
function haskey(h,k)= len([for( i=[0:2:len(h)-2]) if(h[i]==k)k ])>0;
function kidx(h,k)=  //= index of k in keys(h)
    [for(i=[0:2:len(h)-2]) if(h[i]==k)i/2][0];
function hashkvs(h)= [for(i=[0:2:len(h)-2]) [h[i],h[i+1]]];
>>> h = ["a",1,  "b",2, 3,33];
>>> hashkvs(h); // [["a",1],["b",2],[3,33]]

function delkey(h,k)=    
(
   h?[ for(i=[0:len(h)-1])  
     if((i%2==0 && h[i]!=k)||(i%2!=0 && h[i-1]!=k)) h[i] 
   ]:[]
);     
function delkeys(h,ks)= 
( 
   h?[ for(i=[0:len(h)-1])  
     if(i%2==0 && !has(ks,h[i])||(i%2!=0 && !has(ks,h[i-1]))) h[i] 
   ]:[] 
); 

function update(h,g)=
(
  !g? h //<=============== this line added 2015/3/17
  :!h? g //<=============== this line added 2015/6/10
  :[ for(i2=[0:len(h)+len(g)-1])      // Run thru entire range of h + g
      let(is_key= round(i2/2)==i2/2  // i2 is even= this position is a key
         ,is_h = i2<len(h)           // Is i2 currently in the range of h ?
         ,cur_h = is_h?h:g           // Is current hash the h or g?
         ,cur_i = is_h?i2:(i2-len(h)) // Convert i2 to h or g index
         ,k= cur_h[ is_key?cur_i:cur_i-1 ]  // Current key
         ,overlap = kidx((is_h?g:h),k)>=0   // Is cur k-v overlap btw h & g?
      )
      if( !(overlap&&!is_h)) // Skip if overlap and current hash is g
         is_key? k
               : overlap?hash(g,k):cur_h[cur_i]    
   ]
);
```
   ==> [Menu](#menu) 

---
### ichar

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Function| **ichar**( *s,c* ) | [Parkinbot](http://forum.openscad.org/taking-customizer-input-and-using-it-in-a-pair-of-nested-loops-tp23921p23935.html) | Return index of char (but not substr) in a str|

```c++
function ichar(s,c) = search(c, s, 0)[0][0];
```
   ==> [Menu](#menu) 
   
---
### Line

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Module| **Line**( *pts* ) | Inspired by [Ronaldo](http://forum.openscad.org/Can-you-sweep-a-object-with-fingers-tp19057p19330.html) | Much more efficient than a direct hull() of points|

```c++
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
   ==> [Menu](#menu) 


---
### rotate_fixed

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Function| **rotate**( *angle* ) | [nophead](http://forum.openscad.org/Rounding-Errors-tp21821p21834.html) | Fix an issue of the built-in rotate()|

```c++
module rotate(angle)            // built-in rotate is inaccurate for 90 degrees, etc
{
 a = len(angle) == undef ? [0, 0, angle] : angle;
 cx = cos(a[0]);
 cy = cos(a[1]);
 cz = cos(a[2]);
 sx = sin(a[0]);
 sy = sin(a[1]);
 sz = sin(a[2]);
 multmatrix([
  [ cy * cz, cz * sx * sy - cx * sz, cx * cz * sy + sx * sz, 0],
  [ cy * sz, cx * cz + sx * sy * sz,-cz * sx + cx * sy * sz, 0],
  [-sy,      cy * sx,                cx * cy,                0],
  [ 0,       0,                      0,                      1]
 ]) children();
}      
```
==> [Menu](#menu) 


---
### rotate_anydir

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Function| **rotFromTo**( *vi,vo* ) | [Ronaldo](http://forum.openscad.org/rotate-45-45-0-tp24013p24015.html) | Rotate obj from one direction to another (no worry about angle) about an axis passing [0,0,0] |

```c++
module rotFromTo(vi,vo) 
    if( norm(vi-vo)==0 || norm(vi)==0 || norm(vo)==0 ) 
        children();
    else 
        mirror(vo/norm(vo)+vi/norm(vi)) mirror(vi) children();
```
The functions to calc the corresponding rotation matrix:
```c++
function TrotFromTo(vi,vo) =
    norm(vi-vo)==0 || norm(vi)==0 || norm(vo)==0 ? 
        [[1,0,0],[0,1,0],[0,0,1]] :
        Tmirror(vo/norm(vo)+vi/norm(vi)) * Tmirror(vi);

function Tmirror(v) =
    norm(v)==0 ? 
       [[1,0,0],[0,1,0],[0,0,1]] :
       let(u = v/norm(v))
       [ [1,0,0] - 2*u[0]*u, [0,1,0] - 2*u[1]*u, [0,0,1] - 2*u[2]*u ];
```       
==> [Menu](#menu) 


---

### rotate_anyaxis

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Function| **rotObj**(*pq,a*), **rotPts**(*pts,pq,a*)  | Runsun | Rotate obj or points about ANY axis |
```c++
// Rotate an obj: rotObj( pq,a ) obj();
// Rotate points: rotPts( pts, pq, a );
function rotM(pq,a) = 
(  /* 
       Rotation matrix about any arbitrary axis pq.       
       http://www.fastgraph.com/makegames/3drotation/
   */   
   let( /* if we move pq by moving p to ORIGIN, p=>q will be looking
           outward from the ORIGIN. This will result in wrong direction
           of rotation. So we need to reverse it.
        */
        uv = ( pq[0]-pq[1])/norm(pq[1]- pq[0]) // unit vector
      , x=uv[0]
      , y=uv[1]
      , z=uv[2]
      , c=cos(a)
      , s=sin(a)
      , t=1-c
      )
      [ [ t*(x*x)+c,   t*(x*y)-s*z, t*(x*z)+s*y ]
      , [ t*(x*y)+s*z, t*(y*y)+c,   t*(y*z)-s*x ]
      , [ t*(x*z)-s*y, t*(y*z)+s*x, t*(z*z)+c   ]
      ]
);
  
module rotObj( pq, a )
{
    translate( pq[1] ) 
    multmatrix(m= rotM( pq,a) ) 
    {
       translate( -1*pq[1] ) 
       children();
    }           
} 
function rotPt(pt,pq,a)= rotM(pq,a)*(pt-pq[0]) + pq[0] ;
function rotPts(pts,pq,a)= [ for(p=pts) rotPt(p,pq,a) ] ;
```
==> [Menu](#menu) 


--- 
### sortArrs

| Type | API | Source | Remark |
|------|-----|--------|--------|
|Function| **sortArrs**( *arrs,by=0* ) | [runsun](http://forum.openscad.org/Programming-in-Functional-OpenSCAD-tp23039p23280.html) | A quick sort for arrays based on given index. Inspired by [Ronaldo](http://forum.openscad.org/Programming-in-Functional-OpenSCAD-tp23039p23272.html) |

```c++
function sortArrs(arrs, by=0)=
(
  !(len(arrs)>0) ? [] : 
    let( pivot   = arrs[floor(len(arrs)/2)][by],
           lesser  = [ for (y = arrs) if ( y[by]  < pivot ) y ],                                        ,
           equal   = [ for (y = arrs) if ( y[by] == pivot ) y ] ,
           greater = [ for (y = arrs) if ( y[by]  > pivot ) y ]
       )
      concat( sortArrs(lesser, by), 
              equal, 
              sortArrs(greater, by) 
            )
);

arrs = [[2.9, 1.9, -2.8], [-2.5, -1.5, -2.9], [-0.1, 2.8, 2.4], [0.9, 1.8, 
0.8], [-1, -1.3, -0.8]] ;

sortArrs(arrs,by=0):

 [[-2.5, -1.5, -2.9] 
, [-1, -1.3, -0.8] 
, [-0.1, 2.8, 2.4] 
, [0.9, 1.8, 0.8] 
, [2.9, 1.9, -2.8]] 

sortArrs(arrs,by=1):

[[-2.5, -1.5, -2.9] 
, [-1, -1.3, -0.8] 
, [0.9, 1.8, 0.8] 
, [2.9, 1.9, -2.8] 
, [-0.1, 2.8, 2.4] 
] 

sortArrs(arrs,by=2):

 [[-2.5, -1.5, -2.9] 
, [2.9, 1.9, -2.8] 
, [-1, -1.3, -0.8] 
, [0.9, 1.8, 0.8] 
, [-0.1, 2.8, 2.4]] 

```
   ==> [Menu](#menu) 
   


   
