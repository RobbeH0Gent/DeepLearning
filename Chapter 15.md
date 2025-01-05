# Processing sequences using RNNs and CNNs

* gaat vooral over sequenties
  - CNNs -> 1 dimensie
  - RNNs -> vroeger hot topic, nu niet meer

* Fully connected netwerken
  - problemen:
    * verwacht vaste grootte van een netwerk
    * geen concept van "volgorde"

* Voorbeelden van sequenties
  - Tijdsreeksen: waarde van een aandeel raden op die datum
  - Natuurlijke taal: positieve of negatieve tweet, ham of spam
  - Geluid:
 
* Problemen van RNNs
  - onstabiele gradiënt
  - moeite met geheugen op lange termijn
  - inherent sequentieel (moeilijk te paralelliseren -> trainen gaat traag)
 
![image](https://github.com/user-attachments/assets/8d83c42d-4bb9-40e0-80ea-05224da45726)
* Wat doet zo een 'blokje'?
  - Terugblik naar Dense netwerk: een activatiefunctie toegepast op XW + b
  - RNN: ![image](https://github.com/user-attachments/assets/1d11b2d5-7850-473a-873e-15426f550e4e)
    * X(t): (Batch dimensie, feature dimensie)
    * ^Y(t): (Batch dimensie, output)
    * Wx: (feature dimensie, output)
    * Wy: (Ouput, Output) (vierkante matrix)
    * b: (output, )
   
    * ![image](https://github.com/user-attachments/assets/b2ac601e-2760-40c8-957b-06248895f5a7)
    * hier komt een functie uit van alle voorgaande Xen
    * ![image](https://github.com/user-attachments/assets/46becfe9-6009-45ca-bf17-25936d636ddc)

* Seq-2-vec (classificatie van een natuurlijke taal)
  ![image](https://github.com/user-attachments/assets/61047f8d-0bb3-45a4-9cfd-ff2ceef7cd17)

* Seq-2-seq (Voorspellen van een tijdsreeks, op elk moment voorspel je al wat er morgen gebeurd)
  ![image](https://github.com/user-attachments/assets/eec5260b-d408-4877-a79e-5628ff759457)

* Vec-2-seq (Image captioning) (netwerk beschrijft wat er op de foto staat, bv. 2 mensen wandelen met een hond in park)
  ![image](https://github.com/user-attachments/assets/0f9ca9a7-75dc-40a3-aaa9-6515e7ef06d6)

* Encoder-decoder (vertalen van natuurlijke taal, je kan zinnen niet goed vertalen met een seq-2-seq)
  - Encoder: input_zin
  ![image](https://github.com/user-attachments/assets/4b0702b0-7068-4ee3-9a79-185dc8045f6c)


## Window methode

![image](https://github.com/user-attachments/assets/de1b5b1c-0edf-4e74-a64a-39b40cd1e069)

## Flat_map methode

![image](https://github.com/user-attachments/assets/1b410544-4ccd-434d-8b22-2dd1cee564ca)


## Verschillen tussen de modellen

![image](https://github.com/user-attachments/assets/681a012a-29ce-420e-9e84-7c911da610e6)


## WaveNet
* dilation_rate=2 (standaard (kijk links) =1)
* ![image](https://github.com/user-attachments/assets/86468361-5a5f-4888-b85c-773b33b9bacd)
* door causal padding kijk je nooit in de toekomst



