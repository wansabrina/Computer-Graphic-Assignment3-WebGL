# Assignment 3 Grafika Komputer - WebGL
| Nama                   | NRP          |Kelas          |
|------------------------|--------------| --------------|
| Wan Sabrina Mayzura    | 5025211023   | A             |

## Soal 1
Dari kode template RGB Triangle, ubah bentuk segitiga menjadi segi empat (Square)

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/blob/main/documentation/image.png)

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-1.png)

### Solusi
Buat 2 segitiga yang sama, namun rotate segitiga tersebut sebesar 180° dan sesuaikan koordinat beserta warnanya.

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-11.png)

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-12.png)

```
/* SET UP FOR FIRST TRIANGLE */
/* Set up values for the "coords" attribute */
let  coords1 = new Float32Array( [ -0.5,-0.5, 0.5,0.5, -0.5,0.5 ] );
            
gl.bindBuffer(gl.ARRAY_BUFFER, bufferCoords);
gl.bufferData(gl.ARRAY_BUFFER, coords1, gl.STREAM_DRAW);
gl.vertexAttribPointer(attributeCoords, 2, gl.FLOAT, false, 0, 0);
gl.enableVertexAttribArray(attributeCoords); 
            
/* Set up values for the "color" attribute */
let  color1 = new Float32Array( [ 0,1,0, 1,0,0, 0,0,1 ] );
         
gl.bindBuffer(gl.ARRAY_BUFFER, bufferColor);
gl.bufferData(gl.ARRAY_BUFFER, color1, gl.STREAM_DRAW);
gl.vertexAttribPointer(attributeColor, 3, gl.FLOAT, false, 0, 0);
gl.enableVertexAttribArray(attributeColor); 
             
/* Draw the triangle. */
gl.drawArrays(gl.TRIANGLES, 0, 3);
         
/* SET UP FOR SECOND TRIANGLE */
/* Set up values for the "coords" attribute */
let coords2 = new Float32Array([-0.5,-0.5, 0.5,0.5, 0.5,-0.5]);
            
gl.bindBuffer(gl.ARRAY_BUFFER, bufferCoords);
gl.bufferData(gl.ARRAY_BUFFER, coords2, gl.STREAM_DRAW);
gl.vertexAttribPointer(attributeCoords, 2, gl.FLOAT, false, 0, 0);
gl.enableVertexAttribArray(attributeCoords); 
            
/* Set up values for the "color" attribute */
let color2 = new Float32Array([0,1,0, 1,0,0, 1,1,1]);
         
gl.bindBuffer(gl.ARRAY_BUFFER, bufferColor);
gl.bufferData(gl.ARRAY_BUFFER, color2, gl.STREAM_DRAW);
gl.vertexAttribPointer(attributeColor, 3, gl.FLOAT, false, 0, 0);
gl.enableVertexAttribArray(attributeColor); 
             
/* Draw the triangle. */
gl.drawArrays(gl.TRIANGLES, 0, 3);
```

### Output
![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-2.png)

## Soal 2
Dari kode template 2D Cube, ubah bentuk kubus koordinat 2D menjadi kubus koordinat 3D, dan tunjukkan sisi-sisi dari kubus tersebut.
![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-3.png)

```
drawPrimitive( gl.TRIANGLE_FAN, [0,1,0,1], [ -0.5,-0.5,-0.5, -0.5,0.5,-0.5, 0.5,0.5,-0.5, 0.5,-0.5,-0.5 ]);
drawPrimitive( gl.TRIANGLE_FAN, [1,0,0,1], [ -0.5,-0.5,0.5, 0.5,-0.5,0.5, 0.5,0.5,0.5, -0.5,0.5,0.5 ]);
drawPrimitive( gl.TRIANGLE_FAN, [0,0,1,1], [ -0.5,0.5,-0.5, -0.5,0.5,0.5, 0.5,0.5,0.5, 0.5,0.5,-0.5 ]);
drawPrimitive( gl.TRIANGLE_FAN, [1,1,0,1], [ -0.5,-0.5,-0.5, 0.5,-0.5,-0.5, 0.5,-0.5,0.5, -0.5,-0.5,0.5 ]);
drawPrimitive( gl.TRIANGLE_FAN, [1,0,1,1], [ 0.5,-0.5,-0.5, 0.5,0.5,-0.5, 0.5,0.5,0.5, 0.5,-0.5,0.5 ]);
drawPrimitive( gl.TRIANGLE_FAN, [0,1,1,1], [ -0.5,-0.5,-0.5, -0.5,-0.5,0.5, -0.5,0.5,0.5, -0.5,0.5,-0.5 ]);
```

### Solusi
Ubah koordinat menjadi 

```
// Front Faces (Green)
drawPrimitive( gl.TRIANGLE_FAN, [0,1,0,1], [ -0.5,-0.5,-0.5, -0.5,0.3,-0.5, 0.3,0.3,-0.5, 0.3,-0.5,-0.5 ]);
// Front Faces (Green)
drawPrimitive( gl.TRIANGLE_FAN, [1,0,0,1], [ -0.5,0.3,0.5, -0.3,0.5,0.5, 0.5,0.5,-0.5, 0.3,0.3,-0.5 ]);
// Top Faces (Green)
drawPrimitive( gl.TRIANGLE_FAN, [0,0,1,1], [ 0.3,-0.5,-0.5, 0.3,0.3,-0.5, 0.5,0.5,-0.5, 0.5,-0.3,-0.5 ]);
// Right Faces (Green)
drawPrimitive( gl.TRIANGLE_FAN, [1,0.5,0,1], [ -0.5,-0.5,0.5, -0.3,-0.3,-0.5, 0.5,-0.3,-0.3, 0.3,-0.5,-0.5 ]);
// Bottom Faces (Green)
drawPrimitive( gl.TRIANGLE_FAN, [1,1,0,1], [ -0.5,-0.5,0.5, -0.3,-0.3,0.5, -0.3,0.5,0.5, -0.5,0.3,0.5 ]);
// Back Faces (Green)
drawPrimitive( gl.TRIANGLE_FAN, [1,0,1,1], [ 0.5,-0.3,0.5, -0.3,-0.3,0.5, -0.3,0.5,0.5, 0.5,0.5,0.5 ]);
```

### Output
![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-4.png)

Untuk menunjukkan masing-masing sisi, jadikan keenam sisi lainnya menjadi komentar, kecuali sisi yang ingin ditampilkan. Contoh untuk menampilkan sisi depan saja:
```
// Front Faces (Green)
   drawPrimitive( gl.TRIANGLE_FAN, [0,1,0,1], [ -0.5,-0.5,-0.5, -0.5,0.3,-0.5, 0.3,0.3,-0.5, 0.3,-0.5,-0.5 ]);
// Top Faces (Red)
// drawPrimitive( gl.TRIANGLE_FAN, [1,0,0,1], [ -0.5,0.3,0.5, -0.3,0.5,0.5, 0.5,0.5,-0.5, 0.3,0.3,-0.5 ]);
// Right Faces (Blue)
// drawPrimitive( gl.TRIANGLE_FAN, [0,0,1,1], [ 0.3,-0.5,-0.5, 0.3,0.3,-0.5, 0.5,0.5,-0.5, 0.5,-0.3,-0.5 ]);
// Bottom Faces (Orange)
// drawPrimitive( gl.TRIANGLE_FAN, [1,0.5,0,1], [ -0.5,-0.5,0.5, -0.3,-0.3,-0.5, 0.5,-0.3,-0.3, 0.3,-0.5,-0.5 ]);
// Left Faces (Yellow)
// drawPrimitive( gl.TRIANGLE_FAN, [1,1,0,1], [ -0.5,-0.5,0.5, -0.3,-0.3,0.5, -0.3,0.5,0.5, -0.5,0.3,0.5 ]);
// Back Faces (Magenta)
// drawPrimitive( gl.TRIANGLE_FAN, [1,0,1,1], [ 0.5,-0.3,0.5, -0.3,-0.3,0.5, -0.3,0.5,0.5, 0.5,0.5,0.5 ]);
```
Sisi depan

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-5.png)

### Sisi Lainnya
Sisi atas

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-6.png)

Sisi kanan

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-7.png)

Sisi bawah

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-8.png)

Sisi kiri

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-9.png)

Sisi belakang

![Alt text](https://github.com/wansabrina/Computer-Graphic-Exercise2-WebGL/raw/main/documentation/image-10.png)
