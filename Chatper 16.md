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



