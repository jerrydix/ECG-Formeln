# ECG Formeln
## Darstellung vertices
- v: vertex index
- x,y,z: coordinates (world)
- C: color at vertex in rgb
- T: texture coordinate at vertex (u,v)
- N: normal at vertex
- t: triangle index
- i,j,k: 3 Eckpunkte of triangle (using v: vertex index)
![[vertices_darstellung.png]]
## TRANSFORMATION PIPELINE
![](https://lh3.googleusercontent.com/2UfnN-PTZI1cOQrscUWYVxRz9YOZkaJO0QPKQOpmBiF33Ypcx1qiY1zebzJ073J2XO970EU-7ZH1NJRaKUlO-5Llri6Ys4aaolpo9RGvn1uRXyYzl2fT_IIqxjaTDTbkEyjYOp7XZ9QhtlrLsuqlQpo)

![](https://lh6.googleusercontent.com/D_Heb4Djpk8aZ8qWMl-pgPbnSlx8cYIR2O9m179_Nz-8c09qQTzJljGN5o9SeiZcI5ddqG0U7tQjAWlvTZSHGRrNqNtPhICfypDx0G6fxnS5k1X67w0nDifN_GYtiSGevvU2ib87hpq21uAH6C_HUFY)
## Barycentric Coordinates / Interpolation
Point has to have coordinates between 0 and 1 to be inside traingle, else it is outside of the triangle
![[barycentric_coords.png]]
Matrix mit [P1,P2,P3] mit [P] auf rechter seite -> gauss -> (alpha1, alpha2, alpha3)^T

## Lambertian (diffuse at rough material)
- Ir (x, wr): light intensity at surface point x, (reflection vector wr (called mirror reflection))
- kd: diffuse material constant (either 0 or 1)
- n: normal vector at surface point (unit length / normiert: 1/|n| * n)
- l: vector from surface point to light source (unit length / normiert: 1/|l| * l)
- Ii: light intensity of light source

![](https://lh4.googleusercontent.com/OUq2kn86oYEf2o8afOSdsTnbwZWGDD8jG5fowL49FUL89HW-vNstPZrGAQNJBk_AaqoOc4DvgfXHZzPW3t_JyKa9QtMuTYSOFA2h3ABN-s9SeA2ollcNWC3MyrVoNOznuLbX_BEevDKC1Foc_d3nGbM)

## Specular (glossy, reflection at smooth material)
- v: vector form surface point to viewer / camera (Einheitsvektor)
- n - vektor: normal vector at surface point (unit length / normiert: 1/|n| * n)
- l: vector from surface point to light source (l = light src point - surface point) (unit length / normiert: 1/|l| * l)
- r: ideal reflection vector (Einheitsvektor)
![[reflection_vector_formula.png]]
- Ii: light intensity of light source
- ks: specular material constant (either 0 or 1)
- n: specular exponent, controls extend of highlights (je groesser desto kleiner ist das helle feld)

![](https://lh5.googleusercontent.com/ffdWOYcmUwQKD14sH31zHpKj6fyq-9sYUBrWEgwMySO7KL_wMbip3OPtd2BgOhTxzGDQXB2aTH8BY3DEXs0EyXNHfNzeRcTOPgtYRlq5ufh1-AjbFM93HDLWI0pg6C_l-LFVVwyOXeMvKi4WBsdEnHw)

## Phong (light intensity):
![](https://lh6.googleusercontent.com/-sN5uhG8ddFvVdA2fC7Z7bf34mO1oTYusPz5G4pzj54WZkkG1Tw7xQIXjYBIobtBmBh15v2VAZwbgjdifyN7NGJX8Si5z4qNkkcrUedn3jc5FRBDnhuGF6mr2gEdSppAV1UIlrs1hSRsplFGmpLKpQg)
- l: vector from surface point at light source (l = light src point - surface point) (unit length / normiert: 1/|l| * l)
- n - vektor: normal vector at surface point (unit length / normiert: 1/|n| * n)
- r: ideal reflection vector
![[reflection_vector_formula.png]]

## Phong (with color):
- l: vector from surface point at light source (l = light src point - surface point) (unit length / normiert: 1/|l| * l)
- n - vektor: normal vector at surface point (unit length / normiert: 1/|n| * n)
- r: ideal reflection vector
- v: vector form surface point to viewer / camera
- n: specular exponent, controls extend of highlights (je groesser desto kleiner ist das helle feld)
![](https://lh3.googleusercontent.com/qqbtvoJ8IFpgB-fi2yjrPiiuLz9rTMBS24nukyhXqwfCrHGhck1w_m-hCHWCnnKCl0vA3zUU5ilWmKo_9TJt38SurJOP5QjDyhkj8MXHftCCUAt8iO_XowUzYNkrOs4Q0uDpoPNSC4X5ZJiTUzeNdN0)

## Viewing transformation:
![[viewing_transform_1.png]]
![[viewing_transform_2.png]]
![[viewing_transform_3.png]]
- Move camera C to origin=Translation by 
- C: Mtrans -Build orthonormal camera frame=„right“: R = DxU, „zenith“: U = RxD (only if U, D are not orthogonal)
- Adjust orientation: 𝑀𝑣𝑖𝑒𝑤= [R,U,D]^(-1) Mtrans 
- modelview transformation 𝑀 = 𝑀𝑣𝑖𝑒𝑤*𝑀𝑚𝑜𝑑 
- objects now in view space, transforms vertices and normals 
- v is given by the difference of two points v0,v1 
- v´ = (Mv0) - (Mv1) = M(v0-v1) = Mv -n´=Qn -Q = (M-1)^T


## Perspective projection:
-   1: z component goes to 4th component of result vector
-   2: divide by 4th component

**![](https://lh6.googleusercontent.com/AVQ0rQVGTwffAtRlDEJ48rftAvJifOEEMcsL6okl7lgbujiSi6aAFC9me0cS2JjpyvMcyvbmXaMloCnXSzmppFQlh7T2o0tTJnMk5Ev9Gv8l9emiLSfUa6dYfHye1LKWS0st-bUajj5FQaMdGxr3oJw)**
**![](https://lh6.googleusercontent.com/AVQ0rQVGTwffAtRlDEJ48rftAvJifOEEMcsL6okl7lgbujiSi6aAFC9me0cS2JjpyvMcyvbmXaMloCnXSzmppFQlh7T2o0tTJnMk5Ev9Gv8l9emiLSfUa6dYfHye1LKWS0st-bUajj5FQaMdGxr3oJw)****

Matrix representation of the standard projection onto the z = 1 plane
-   1: z component goes to 4th component of result vector
-   2: divide by 4th component

![](https://lh4.googleusercontent.com/dWyZV9FTczsvcXuU5i8gOuZmEFhPWmB0YkS9WVafxuo_QtrBsW6Li7xZXfBeK1UPM98RIEYCod3xgcmFTa5fSNz7G_NqzR6FyVPkqB-rPrBI3FoCqvAnt5ixv6O-ryL4iu2ez5Fu-RQ_3D92rAZ03Sw)**![](https://lh4.googleusercontent.com/7de8TMNyPMarOPKYEXMi-w9Y60QJk59-rJ1REkdWSCUDMAbuHQx_9ungzy6_Fh3ckJGSnh8RwiKPGTifZsCL1QRCnXEarr-2hnVO7mABZ7GAcjpWrov0bb0FfZYQ11H0zjg9G6UaFzhaB3PEhECKL5Q)![](https://lh3.googleusercontent.com/zdG4EnX8-UjZAV-8LgSuDUAqxRd7thPSj9fnB_0ttfVuZcloU5tN4RxcOu3liD5w4V3Q4HHcqxnk7OUirw63CjCiO5iZueDSJmoTJzvdH8icKfa-7K6MWt1BGdyaupJ9jahqgo5nkxmu6BDLwZg9XWM)

### Projection matrix
1.  Scaling: scale fov to -1 to 1
2.  Scaling: scale depth range to 0 to 1
3.  Translation: move z-near to 0, z-far to 1
4.  Prepare for division: Put z into w (dummy) component

**![](https://lh5.googleusercontent.com/IBdjW2ONlNlJ53ytZUXOb7YhCeAVcCSgzlTBGVysbA0kxFZTaI9BPsEslBtKW0ySw24ZKEg5ztf2wk_BVocbOqsiCGjGo9sl0jSy6QWxpeGU_SAdnSEbkBDDFJErL-ibHRMu5KElwe9Zd11aqV_8ox8)**
**![](https://lh3.googleusercontent.com/nMNiUY1a0q2NyAByQS4oPzqZc7xLWUPNhOmFmwwlWI_20UTiPRQ5-7hR6xfqQg_vDab5KKD9uKdwPVl2a_LeQVfExqbrYxmLTzT42qRJZo7GOw5RuedZ_tINRq1AS6z0O9PCEqG_PLXaCIVojq1eSuM)**

#### API projection matrix
**![](https://lh5.googleusercontent.com/DceyTBaqs6xULXtAqkZoAKaMv9hr7XUcamRTSs-Q6R9oS4yBXvErbv9DxWakefm2nnySo6ZAZJtVTnqEbqKonumuLxUseiBIsq9a3nor7rwVlkwxOLlFhXlEuciKCutTIR-C1jHcA4mHJ_DeJI38W38)**

## Rasterization (viewport transformation matrix)
**![](https://lh4.googleusercontent.com/YWhc0heK0iyhROazw41gyGS69lYXMebbmzDIwBQwY9hRXWEfiNWDqmi61dzR1umfmC6qlW9I7iY7KMbHqp2ar46r4ToLaG0lglXjS6xLjT8lr1El22DMwimDrdLUsgZaOspJsIvZmDdA-HfJ9LFW1to)

### Viewport Transformation Matrix:
**![](https://lh4.googleusercontent.com/MmNNwMY_hbmuYYc0m96PXEcLvlX-_QtdBRTUIWy1lt9uUna1gj8I2gveRuPsc9VdfuRdmChMPcI5783WCuZHKHK6ndzNbMM1SV7W-5IMe6-6whc2y3yTRSNJaguc8o7W30K7LUC2hKqikZsOMWeSqDU)

## Alpha blending

Additive blending: farben werden addiert (alpha * col + alpha * col usw.)
Multiplicative blending: farben werden multipliziert

(src): incoming fragment
(dst): values in colorbuffer

IMPORTANT: Cdst und Csrc sind nur rgb vektoren (ohne alpha)

ALPHA (over for 2 elements): 
given C1 and C2:

Then:
Cd = alpha2 * C2
Cs = alpha1 * C1

C = Cs + (1 - aplha1) * Cd

OVER (back to front): 
**Cdst = Csrc + (1 - Asrc) Cdst**

UNDER (front to back):
**Cdst = Adst (Asrc Csrc) + Cdst**
**Adst = 0 + (1 - Asrc) Adst**

for background: 
**Cdst = Adst Cbg + Cdst**

## Sampling and Aliasing:
- Shannon‘s Sampling Theorem: The signal has to be sampled at a frequency that is larger than two times the highest frequency in the signal
- Supersampling: increase sampling frequency
- Prefiltering: decrease the highest frequency in the signal

## Texture filtering (nearest, bilinear interpolation)
**![](https://lh5.googleusercontent.com/RDfYxzZKLh4jC0L9Kwed8Cb-MmKyby70WhOwTgVIqlyVY_CAzoXy4OEn-gpoI37-ixg-bT8CQZOP6ujG52daZ2QAu_gc48LoX0Wl2IGS0VgePEt0CP2KNfiQUqrxQMA_muxe_EszCcUvmZg0hp0wrZQ)**
A,B,C,D sind Farbvektoren
x,y sind blaue flaeche
## Mipmapping 
![[Pasted image 20220810150413.png]]
**![](https://lh3.googleusercontent.com/MT_A0U4gZ2zAytdWBTwLXzIdg3R7VAHemYrCAGP_BVJHVaZ39f1F6g1FWfSMpa5GtBMGhzOhrLmeymCOcVECvG1O9PIbIbDOudJ0lfb-ctpEw5xmcwwN545WcQv_T0-zk18BwF60OJxg9-U6guTLkZQ)**
### Anisotropic
**![](https://lh4.googleusercontent.com/WF05q0WJJjq6HvsaE4OclBzJFqLs0DoAcQwOXQVmv2yKfULVUphDmCV1Agitx-nb5Xk92ZGQZdO4CPVK4bVhPRhmr11Lh1onTQTPs3UUF8Vg_b6JJBi6ZiRPLggZFDv9MGJrUNuXF-YZfXTte70EGBM)**

## Planar reflection
**![](https://lh4.googleusercontent.com/dWNgDBKUJThY1k9gWcf6-l9D4S8PAb2orHlJHow9ZkoSkaZ3qou25POn8z6cl7Im4hs1dRus0i4aeEZs9vg7spY6NCCmoR8NGzlSYEjSgNIbJoAdg2bCYBZ0tCNXEU--RElBjrWg0KZEnpGnHJCaumo)**![](https://lh6.googleusercontent.com/_uhKvM_frYcAgA3zjXLSlMX4pFTQx_TiiS2rXw1Iv5G1H-fii2Y2Sx42l3jn9BhGzZVLJWWEqSSxTiEc9K1vixURUHQiy8BJfL6DU7EXoEE99s3wKdkpexYELeiDn7dYmqQWwQYCeCTO0vMn2xIlXWo)
**![](https://lh3.googleusercontent.com/PXdWGM3kBvAzxv3ibeDxV8WmSZUYpT7onHnpDq-a5fwsJ_UwHWcemzlhoDscCgxWVL8JwRzgExeJ4a3VDdKba8k8rwGwtJEcfsV_SHU-fp1o-TnbW--dBOCAJ-aRNVRj95CmY_KV3xR65uT88Fjr0Hc)**

## Cube map access
**![](https://lh4.googleusercontent.com/CGCJg6RpNP1ZCN4MzsyLtTkBM0BzXvZqg_7ax-CBpHY5tv0ry4pBIbaSYnpKGC-V3IUsA8-Iop3y5LaN9zmmYTUZVGIP_S4DTrDt0n3gFdSQedsFgSTHzaQbzHkbjEtjGqNRwfyn7dgXXfg2DVNuATU)**
**![](https://lh5.googleusercontent.com/rt2ThHI85Q5F3W2MTVOej7Xnoo8AfzhQDdpWMRd5nvETuYxgjYRVl1m34SprRKlW1KU6JFi_drZfvGQIZHg-psIG-ZU3PeBg7HN21DprhaY_zfF40wnv-20Y-9xlITOnS0oPclHKdIIDawC0k5B0DSc)**

## BVH traversal
- bounding volume hierarchy)
- (axis aligned bounding boxes)

**![](https://lh4.googleusercontent.com/6nzhvBs5ljqTdvdtXy6N6WERMMWbjovH-p_XCUSGHIx2IUYdx3XMcso_O9kC3z8vClJ74mIngCxQXUuAwqVYHiDoy4Y_O1uLFyf4w9gKzDbCMQEdsKorf6lpKue8js0CyiMM7T6x5QkBV0GMCZ0qZxA)**

## SAH (Surface Area Heuristic)
- given the world, we want to split it into two subsets: A and B
- there is a cost associated to that (we want to minimize that cost)

- Sum of Ci(a): cost of intersecting all primitives of A 
- Sum of Ci(b): cost of intersecting all primitives of B

- pA: probability to hit any of the primitives of A  
- pB: probability to hit any of the primitives of B  

Heuristic (approximation of pA and pB):
- pA is the surface area of A relative to bounding box above it    
- pB is the surface area of B relative to bounding box above it 

**![](https://lh4.googleusercontent.com/VfjfP-tw8SAS6wXbOXxSLE_JCMMftntMRhFCKZlwN-sYdDMbmezGl4cshz1GbdXwt9xBGx1cGPBmQOWWsCEvJ2b2RcHMqx3VFienVi4nRfmoXcbnyeM2zgo6SeUPm0-YaXPMWElDEM54VIF2PlUur2w)**
**Example: ![](https://lh5.googleusercontent.com/2bnpFKw5Udwp8YGZFTorxP2H211VAZZtev88vsAxrpW-x_PyhC7MH64KztjFBZErW2aY_fJXw7m7QbMTN61wP-FbmfufjJ0NxzqD1QVMelyVMMNjSXIH5gtxWldVlK3QhqhE3gTOGpZaQrZNmn9bt50)
BVH REFIT SEE FOLIEN

## Transformations
![[Pasted image 20220805143745.png]]

![[Pasted image 20220805191041.png]]
![[Pasted image 20220805191106.png]]
![[Pasted image 20220805191131.png]]
