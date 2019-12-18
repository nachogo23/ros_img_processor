## ros_img_processor
Just a simple template node receivng an image and doing something. Links to OpenCV and ROS wrapped.

## How to run the code
In a terminal window, type:
```sh
$ roslaunch ros_img_processor ros_img_processor.launch
```

## Tip
Check your webcam encodings (yuyv,mjpeg,...) and set them accordingly at file launch/usb_camera.launch

Repositori original:https://github.com/beta-robots/ros_img_processor

Inicialment el node ens permet veure en pantalla la imatge original de la webcam (image_row) i la imatge rectificada(image_out) seguint els parametres després d'haver fet la calibració. Es dibuixa també un quadrat al centre de la imatge. D'altra banda amb rviz es mostra un eix cartesià de cordenades amb un vector fixe representat.

S'hafegeix part del codi del paquets circle_cedection per mostrar a la imatge rectificada (image_out), la detecció de cercles. Es fixa el paràmetre min_dist a un valor alt (10000) per asegurar que només es detecti un cercle en l'area de la imatge.

S'utilitza un objecte de tipus vector (direction_) corresponent al vector normal al pla de la circumferencia mostrada en la imatge webcam. Per generar el vector es fa servir la matriu "matrixK" invertida i multiplicada per un punt previament definit al centre de la circumferencia. Les tres components del vector es mostren a la terminal per a cada instant.

Aquest vector director de l'esfera (direction_) és substitueix pel vector fixe que s'estava representant a rviz inicialment, com que aquest nou objecte és dinàmic, el vector es mourà a rviz cada cop que canvii l'orientació del cercle detectat. Així es podrà visualitzar en viu el vector normal a la superficie.

D'altra banda s'hafegeix un objecte de representacio de tipus "cv::arrowedLine" per tal de mostrar el vector director (director_) a la imatge mostrada en pantalla (image_out), concretament es situal l'origen del vector al centre de la circumferència. Com que el vector director es unitari és multiplica per un factor per tal de visualitar-lo correctament.

S'adjunten un parell de captures al repositori per demostrar el funcionament del node.


Referencies:
https://docs.opencv.org/2.4/modules/core/doc/drawing_functions.html
