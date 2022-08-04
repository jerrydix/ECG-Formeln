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
![[barycentric_coords.png]]

## Lambertian (diffuse at rough material)
- Ir (x, wr): light intensity at surface point x, (reflection vector wr (called mirror reflection))
- kd: diffuse material constant (either 0 or 1)
- n: normal vector at surface point (unit length / normiert: 1/|n| * n)
- l: vector from surface point to light source (unit length / normiert: 1/|l| * l)
- Ii: light intensity of light source

![](https://lh4.googleusercontent.com/OUq2kn86oYEf2o8afOSdsTnbwZWGDD8jG5fowL49FUL89HW-vNstPZrGAQNJBk_AaqoOc4DvgfXHZzPW3t_JyKa9QtMuTYSOFA2h3ABN-s9SeA2ollcNWC3MyrVoNOznuLbX_BEevDKC1Foc_d3nGbM)

## Specular (glossy, reflection at smooth material)
- v: vector form surface point to viewer / camera
- n - vektor: normal vector at surface point (unit length / normiert: 1/|n| * n)
- l: vector from surface point to light source (l = light src point - surface point) (unit length / normiert: 1/|l| * l)
- r: ideal reflection vector
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