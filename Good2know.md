# Chapter 10

* X = matrix v/d input.
* W = weight matrix.
* b = bias vector.
* $\Phi$ = activation function (phi).
* n = # features.

hieruit kan je dus afleiden:

stel je hebt n = 2, dan geldt als volgt: $\Phi$(b + w1x1 +w2x2)

* Waarom zijn activatiefunctie nodig/nuttig?
  - activatiefuncties zijn nodig om niet lineaire functies te leren

### Coderen C10
* epoch = alle voorbeelden 1x bekijken
* shape=(4,) geeft een tuple terug, shape=(4) geeft een int terug
* Dense layer is een volledig geconnecteerde laag en doet eigenlijk de XW + b
* Softmax wordt berekent als volgt:
  - logits (getal)
  - exp(getal)
  - exp(getal) / som vd exp(getallen)
  - controleren kan je door de som van de softmax te nemen en die moet 1 zijn 

* naar one-hot labels converteren: **keras.utils.to_categorical()**
  - keras.utils.to_categorical([0, 5, 1, 0], num_classes=10)
  - array([[1., 0., 0., 0., 0., 0., 0., 0., 0., 0.],[0., 0., 0., 0., 0., 1., 0., 0., 0., 0.],[0., 1., 0., 0., 0., 0., 0., 0., 0., 0.],[1., 0., 0., 0., 0., 0., 0., 0., 0., 0.]])
* van one-hot labels converteren: **keras.ops.argmax()**
  - keras.ops.argmax(    [[1., 0., 0., 0., 0., 0., 0., 0., 0., 0.],     [0., 0., 0., 0., 0., 1., 0., 0., 0., 0.],     [0., 1., 0., 0., 0., 0., 0., 0., 0., 0.],     [1., 0., 0., 0., 0., 0., 0., 0., 0., 0.]],    axis=1)
  - <tf.Tensor: shape=(4,), dtype=int32, numpy=array([0, 5, 1, 0],dtype=int32)>

* X_train[:, :5]
  - selecteert alle rijen
  - selecteert de eerste 5 kolommen
