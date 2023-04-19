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
mogrify -path ../background -format png -fill "#DFDFDF" -opaque "#8DA131" *.png

# Quitar color del iPhone
mogrify -format png -fuzz 20% -fill transparent -opaque "#8DA131" change.png
mogrify -format png -fuzz 20% -fill transparent -opaque "#CADF8E" change.png
mogrify -format png -fuzz 20% -fill transparent -opaque "#E5F4FE" change.png
mogrify -format png -fuzz 20% -fill transparent -opaque "#FFFFFF" change.png



# Nuevo Intento 
# Convertir Screenshots y cambiarles el tamaño
for file in *.jpeg; do convert $file -resize 640x $file.png; done
# Mezclarlos con el iPhone

mogrify -path ../background/ -format png -fuzz 1% -fill SkyBlue -opaque "#DFDFDF" *.png


=======================================================================
# Pasos
# Convertir Screenshots y cambiarles el tamaño
for file in *.png; do convert $file -resize 640x ../small/$file; done
# Agregarles un borde para que cuadren perfecto con el iPhone
cd ../small
for file in *.png; do convert $file -border 180x192 ../bordered/$file; done
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
mogrify -format png -fill GhostWhite -opaque "#DFDFDF" *.png
cd ../background
# Bajarles el tamaño
for file in *.png; do convert $file -resize 640x ../iphonefinal/$file; done
=======================================================================


# Pasos para meter 2 iPhones en una imagen ============================
# Primero se les quita el margen 
# Pasamos a la carpeta crop las que necesitemos que vayan dobles
magick IMG_0612.png -crop 800x1460+100+158 mix.png

for file in *.png; do magick $file -crop 800x1460+100+158 cropped/$file; done
cd cropped 
# Ahora las pegamos
magick IMG_0612.PNG IMG_0613.PNG +append  mix.png
magick IMG_0618.PNG IMG_0619.PNG +append  mix2.png
magick IMG_0621.PNG IMG_0622.PNG +append  mix3.png

# Agregar Bordes
for file in mix*.png; do convert $file -border 220x192 bordered/$file; done
# Agregar Watermark
cd bordered
for file in *.png; do composite -geometry +1700+1600 ../../../../logoVertical.png $file watermarked/$file; done
# Agregar Color
mogrify -path background/ -format png -fill GhostWhite -opaque "#DFDFDF" *.png


=======================================================================================
# Pasos sin dejar tanto mugrero 
# Empezamos en Screenshots 
for file in *.png; do convert $file -resize 640x iphone/$file; done
# Nos vamos a iPhone
cd iphone
for file in *.png; do convert $file -border 180x192 $file; done
for file in *.png; do composite -geometry +0+0 ../../iPhonem.png $file $file; done
# Agregamos canvas
for file in *.png; do convert $file -border 300x0 -bordercolor none ../canvas/$file; done
# Nos movemos a canvas
cd ../canvas
for file in *.png; do composite -geometry +1200+1600 ../../logoVertical.png $file $file; done
mogrify -format png -fill GhostWhite -opaque "#DFDFDF" *.png
for file in *.png; do convert $file -resize 640x $file; done

# 2 Juntos sin dejar tanto mugrero =====================================================
# Ponemos las que van en dupla en un mismo directorio 
for file in *.png; do magick $file -crop 800x1460+100+158 $file; done
cd cropped 
# Ahora las pegamos
magick IMG_0612.PNG IMG_0613.PNG +append  mix.png
magick IMG_0618.PNG IMG_0619.PNG +append  mix2.png
magick IMG_0621.PNG IMG_0622.PNG +append  mix3.png

# Agregar Bordes
for file in mix*.png; do convert $file -border 220x192 $file; done
# Agregar Watermark
for file in mix*.png; do composite -geometry +1700+1600 ../../../logoVertical.png $file $file; done
# Agregar Color
mogrify -format png -fill GhostWhite -opaque "#DFDFDF" mix*.png