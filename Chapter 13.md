# Loading en preprocessing data with tensorflow

* dataset = tf.data.Dataset.from_tensor_slices(X)
  - laat uw toe om een tensor om te zetten naar een dataset
  - X[0], X[1], X[2], ... (slicen langs de eerste as)
 
* map
  - ![image](https://github.com/user-attachments/assets/9a9531fd-fde7-472b-9966-2f771aec7b64)

* where
  - ![image](https://github.com/user-attachments/assets/e4180290-8ecd-4d56-b6f5-a7c61981edc7)

* filter
    - ![image](https://github.com/user-attachments/assets/a294fd31-0202-4772-b9d0-1a73a9e70b7a)

* take
  - ![image](https://github.com/user-attachments/assets/0e94a5f1-0332-4527-a2a6-9796ab6a1bb1)
 
* shuffle
  - ! buffer_size
    - ![image](https://github.com/user-attachments/assets/cd2d7460-2ed6-4bb1-ba8b-e8d7f35ce830)
    - ![image](https://github.com/user-attachments/assets/b06bc531-2d15-470f-833f-cfd54ab4358b)
    - ![image](https://github.com/user-attachments/assets/ac2105c8-b57a-4347-863d-caa30276dedd)
    - ![image](https://github.com/user-attachments/assets/b03afd3f-616e-4ad3-b8c1-135f34b3dea5)
    - met buffer_size=1 kan je altijd maar 1 getal kiezen -> wordt niet geshuffeld
    - hoe groter de buffer_size hoe meer RAM geheugen men nodig heeft maar hoe randomer de volgorde
  - ![image](https://github.com/user-attachments/assets/21e5211a-b763-4f16-8265-50f9e3d0d12b)
  - ![image](https://github.com/user-attachments/assets/1ba2fd17-ec5b-482d-b1a0-734d98ef1034)

* Interleave
  - ![image](https://github.com/user-attachments/assets/9c7e24f2-16f1-412b-a952-cbfc1c208b54)


## Layers voor theoretisch examen
* Discretization layer
  - ![image](https://github.com/user-attachments/assets/5b1d56cf-5dcc-4822-9a84-3c279ab02576)

* Categorie Encoding layer
  - ![image](https://github.com/user-attachments/assets/5025af3d-76f5-460b-a8dc-1933f1369e6c)
 
* StringLookUp layer
  - ![image](https://github.com/user-attachments/assets/10ccda91-0616-42cc-bffb-5807014be897)
  - ![image](https://github.com/user-attachments/assets/46b59cde-5e40-42ae-9318-a5474dd8d285)
  - ![image](https://github.com/user-attachments/assets/f9b4741b-f7d0-4e74-b523-20aaccffc786)
 
* The hashing layer
  - ![image](https://github.com/user-attachments/assets/bda179ba-1873-4226-a22e-43b7367ad354)

* Embedding layer
  - ![image](https://github.com/user-attachments/assets/46590dac-5007-44ef-9069-f7e69faea985)
  - ![image](https://github.com/user-attachments/assets/7ea607b5-58ec-415d-93a8-5737b15de79d)

* TextVectorization layer
  - ![image](https://github.com/user-attachments/assets/49595945-eea2-4414-8759-0e416c5a548d)
  - ![image](https://github.com/user-attachments/assets/b6702a7c-6dd8-4e48-916b-4d11f35c66b7)
  - Let op dat er geen '' meer is, want woorden die we niet kennen worden toegevoegd aan onze vocabularium

* Image preprocessing layers
  - ![image](https://github.com/user-attachments/assets/d1f4e4dd-ca4c-4b02-8e9f-baca3839d580)
  - ![image](https://github.com/user-attachments/assets/e6170251-5e1f-4933-8b43-9ae55907d086)
  - ![image](https://github.com/user-attachments/assets/72a87868-ff36-4cd3-9525-67658678e726)

* Image augmentation layers
  - check [https://keras.io/api/layers/preprocessing_layers/image_augmentation/]
  - verschil met preprocessing: augmentation gebeurt alleen als je aan het trainen bent, preprocessing gebeurt altijd


## Tensorflow datasets
* != tf.data.Dataset
* verzameling van Datasets (collectie)
* ![image](https://github.com/user-attachments/assets/8beb1f1e-83ea-4b81-9d3a-eea0e5ba520f)











