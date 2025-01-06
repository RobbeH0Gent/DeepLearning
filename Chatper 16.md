# Natural language processing with RNNs and Attention

![image](https://github.com/user-attachments/assets/ec322550-5036-4484-8b6a-d64763fba22a)

Attention block update de betekenis van een woord -> dit gebeurt door de skip-connection
![image](https://github.com/user-attachments/assets/26ad7df5-ed1c-4a30-9e60-457dbdfc09e1)

![image](https://github.com/user-attachments/assets/1a6375ac-e21e-40f6-a287-4bb401194003)
met:
  - een zin met T-woorden (type String) 5T,) -> Sequentie van woorden
  - Embedding laag
  - (T, E) met E een float -> de vorm is sinds hier een float (Encoder blocken)
  - Dense laag
  - (T, num_tokens)

![image](https://github.com/user-attachments/assets/27f08c7a-e6a2-452f-abe5-c3c9b8e4950b)

* links een voorstelling van de woorden in de zin, zonder context
* rechts een voorstelling van de absolute posities van de tokens in de zin

![image](https://github.com/user-attachments/assets/1bbe79fd-f8b9-4aaa-b460-7360e18b1e25)

Tensor van shape=(T, E)
![image](https://github.com/user-attachments/assets/d4799282-3e8c-484c-85d9-b4f8f613322f)
in keras ligt die Q plat (zeg maar dat de Q de Questions zijn)
![image](https://github.com/user-attachments/assets/16ea4c5c-00e0-4291-a56e-47b755a16344)
![image](https://github.com/user-attachments/assets/ccccf2c5-2db3-4db4-8b17-6b361892a942)
Wq heeft dezlfde vorm als Wk \
De K zijn de keys (antwoorden op de questions)
![image](https://github.com/user-attachments/assets/9837807f-30b0-4384-8677-a1ff5816f928)
![image](https://github.com/user-attachments/assets/5c9a546d-0627-49a3-885c-110381f4fa49)

![image](https://github.com/user-attachments/assets/9b246b93-5e7e-4dde-a464-40df7c58cd95)
![image](https://github.com/user-attachments/assets/9a72e8e6-4993-4eff-a60f-a7cecdf0606d)
De Qs staan in de rijen en de Ks staan in de kolommen
![image](https://github.com/user-attachments/assets/cc6a1e29-2f8d-4811-9d57-454e0599b31b)
Matrix van (T,T) + Softmax per kolom
![image](https://github.com/user-attachments/assets/61977656-bb55-4780-8d6d-baffc94d6882)
Causal masking, woorden die later komen wil je de waarde 0 geven maar anders is de softmax van de kolommen niet meer = 1 \
Daarom geef je al deze waardes - oneindig voordat je de softmax toepast, dan wordt de waarde 0 na de softmax

De V staat voor Value
![image](https://github.com/user-attachments/assets/5c3cc3a0-c4c9-4215-8ec4-e788fcd53c6c)
![image](https://github.com/user-attachments/assets/8fab1d5e-f317-46bf-b080-374e2a8bfe8e)

![image](https://github.com/user-attachments/assets/e859eefe-3fd5-4f4d-b97a-351375b5041d)
![image](https://github.com/user-attachments/assets/f2e1b648-f5d9-478e-8fae-0a87f76a50d5)


![image](https://github.com/user-attachments/assets/32e00a27-e8a2-4606-8198-6950a987f19d)
Add is de skip layer -> deze zal je dus niet in de __init__ moeten coderen \
De Norm is een keras.layers.LayerNormalization()


![image](https://github.com/user-attachments/assets/85924eff-f2d8-4c8c-afc1-80d2b575aae4)
Dit is wat een embedding doet: getal/token afbeelden op een vector


## Multi-headed attantion
1) Attention (laag zonder leerbare parameters)
   - tensor Q, de vraag
   - met T tijdstappen
   - met dq als dimensie
   - ![image](https://github.com/user-attachments/assets/50569822-8e28-47e0-9201-08acbca9a736)
  
   - matrix K, de key
   - met S tijdstappen (is niet altijd hetzelfde als bij Q vandaar S ipv T)
   - en dezelfde dq dimensie
   - ![image](https://github.com/user-attachments/assets/21d5b722-31cb-4c0c-8948-27de6d5e26ba)
  
   - matrix V, de value
   - met S tijdstappen (deze is altijd hetzelfde als bij matrix K)
   - en dv als dimensie, omdat deze anders kan zijn dat die van K of Q
   - ![image](https://github.com/user-attachments/assets/92c9700e-e173-4d2d-a28c-63a11d5b7e84)
  
   - Berekening gebeurt als volgt:
   - ![image](https://github.com/user-attachments/assets/29b088b8-e795-4845-97c8-366bcb3f067a)
   - finaal zal je dus iets krijgen met T rijen en dv kolommen
   - ! Geen leerbare parameters


2) Multi-headed attention
   - ![image](https://github.com/user-attachments/assets/f4b11c2d-3121-46cf-b1e8-e2c8518ae118)
   - Stel h heads
   - ![image](https://github.com/user-attachments/assets/c8474952-c5f2-4383-b211-99f2a07b685f)
   - in de blauw onderlijnde zitten leerbare parameters
   - ![image](https://github.com/user-attachments/assets/fb743adc-faf9-4daf-9aa7-9475412abfb6)
   - ![image](https://github.com/user-attachments/assets/1c057c43-aead-4379-a827-3e706ae76e44)
  
   - Resultaat van de i-de head:
   - ![image](https://github.com/user-attachments/assets/c0f46611-7483-4901-a7f9-41bf443ab2a9)
  
   - Resultaat wordt dan:
   - ![image](https://github.com/user-attachments/assets/2afc34d9-f011-4588-af6d-6821f583517e)
   - Alternatief om R te berekenen:
   - ![image](https://github.com/user-attachments/assets/1728a95b-5e45-476f-9175-4fb96e371fbe)

  
   - Return R

     
Samengevat:
![image](https://github.com/user-attachments/assets/e8fad33a-c6bf-4735-957f-04f82fceb89a)


## 3 types of Normalization
1) Normalization
   - ![image](https://github.com/user-attachments/assets/58e58d43-a6da-4639-9064-7482f0c0919b)
   - om dit te laten werken hebben we broadcasting nodig!
   - gevolg: datamatrix waarbij elke kolom: gemiddelde 0 en stdafwijking: 1 heeft
   - geen leerbare parameters (een leerbare parameter is een parameter die wordt aangepast door gradient descent)
   - de mu en sigma worden berekend door 'adapt'
   
2) BatchNormalization
   - ![image](https://github.com/user-attachments/assets/cc923e2d-7f4d-4f73-ae59-6959c54a82b2)
   - precies op dezelfde manier als standaard normalization maar nu voor een batch ipv de hele set
   - ![image](https://github.com/user-attachments/assets/1e829a6f-9be3-4d2f-9f26-bba534679f01)
   - ook hier maken we gebruik van broadcasting
   - Gamma en beta zijn leerbare parameters (gradient descent)
   - ![image](https://github.com/user-attachments/assets/6fa722af-5fef-44dc-b1e0-1e608fb9884a)
  
   - **Inference:**
   - ![image](https://github.com/user-attachments/assets/fc569f27-2435-4f20-b564-d32c05fdd4c3)
   
3) LayerNormalization
   - ![image](https://github.com/user-attachments/assets/0eb55426-344f-4e80-931b-dbaf8126515a)
   - ook hier zijn de gamma en de beta leerbare parameters
   - deze laag heeft GEEN niet leerbare parameters (alle parameters zijn dus leerbaar)


### Temperature
![image](https://github.com/user-attachments/assets/0f0e18f5-3067-458e-b496-d3d3df5cf426)
![image](https://github.com/user-attachments/assets/b4dd80e3-759c-4869-b167-de31b361e907)
Stappenplan:
  - logits
  - herschaald: logits/temp (rescaled logits)
  - exponent van de rescaled logits
  - softmax toepassen (exp / som van alle exp)
  - softmax controleren door op te tellen uitkomst = 1


### Encoder-Decoder
![image](https://github.com/user-attachments/assets/21c8b378-95d2-45e5-b9a7-b2390e855b8b)
- de mha krijgt een query van de decoder, maar een key en value van de encoder













