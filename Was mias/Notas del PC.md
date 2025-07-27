# psicologo: 
### Sesion:  https://udla.zoom.us/j/7705815895
## Cronograma personal

 - 1 bloque de programacion 
 -  reflexion del dia 
 -  reflexiones que estan en el cuaderno 
## Encodear video para YT 

```
ffmpeg -i "input.mp4" \
-c:v libx264 \
-preset fast \
-crf 18 \
-profile:v baseline \
-level 4.0 \
-pix_fmt yuv420p \
-c:a aac \
-b:a 192k \
-movflags +faststart \
-vf "scale='min(1920, iw)':'min(1080, ih)':force_original_aspect_ratio=decrease,pad=1920:1080:(ow-iw)/2:(oh-ih)/2" \
output.mp4
```
