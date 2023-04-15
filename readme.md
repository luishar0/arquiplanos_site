# Edits all files in directory
for file in *.png; do convert $file -resize 50% small-$file; done

# Switches white to transparent
convert iphone14.jpg -fuzz 20% -transparent white result.png

magick convert -resize 710x datos.png datos.png //Resize screenshot
magick convert -size 795×1579 xc:transparent composite.png //Create canvas
magick composite -geometry +59+48 datos.png composite.png screenOnCnanvas.png // Merge screenshot on canvas
magick composite -geometry +0+0 iphone.png screenOnCnanvas.png prueba2.png // Merge with iPhone

# Convirtiendo los screenshots
for file in *.jpeg; do convert $file -resize 640x small-$file.png; done
# Probando en el iPhone
magick composite -geometry +182+200 small-1.png iPhonem.png screenOnCnanvas.png

# Merge clear and phone
magick composite -geometry +0+0 iPhonem.png screenOnCnanvas.png prueba2.png


=======================================================================
# Pasos
# Convertir Screenshots y cambiarles el tamaño
for file in *.jpeg; do convert $file -resize 640x small/$file.png; done
# Agregarles un borde para que cuadren perfecto con el iPhone
for file in *.png; do convert $file -border 180x192 -bordercolor white ../bordered/$file; done
cd ../bordered
# Mezclarlos con el iPhone
for file in *.png; do composite -geometry +0+0 ../iPhonem.png $file ../iphone/$file; done
cd ../iphone
# Agregarles un borde a los lados para espacio a los lados
for file in *.png; do convert $file -border 300x0 -bordercolor none ../iphonebordered/$file; done
cd ../iphonebordered
# Agregarles Watermark
for file in *.png; do composite -geometry +1200+1600 ../logoVertical.png $file ../watermarked/$file; done
cd ../watermarked
# Ponerles fondo
mogrify -path ../background/ -format png -fill GhostWhite -opaque "#DFDFDF" *.png
# Bajarles el tamaño
for file in *.png; do convert $file -resize 640x ../iphonefinal/$file; done
=======================================================================
convert image.png -background white -alpha remove -alpha off white.png

# Esto fue para quitarle el color al iPhone de Angie
magick change.png  -fill white +opaque black result.png
convert result.jpg -transparent white result2.png

# Pruebas
convert small-1.png -border 180x192 -bordercolor transparent bordered.png #border atempt
magick composite -geometry +0+0 iPhonem.png bordered.png prueba2.png

# Pruebas de fondo 
for file in *.png; do convert $file -background white -alpha remove -alpha off ../background/$file; done
for file in *.png; do convert $file -fuzz 1% -transparent white ../background/$file; done
mogrify -path ../background -format png -fill "#DFDFDF" -opaque "#FFFFFF" *.png



# Nuevo Intento 
# Convertir Screenshots y cambiarles el tamaño
for file in *.jpeg; do convert $file -resize 640x $file.png; done
# Mezclarlos con el iPhone

mogrify -path ../background/ -format png -fuzz 1% -fill SkyBlue -opaque "#DFDFDF" *.png