# VAE   
MNIST data를 학습한 간단한 VAE model    
**MNIST data는 0~1의 값으로 구성되어 있기 때문에, decoder의 output을 sigmoid로써 확률로 나타낼 수 있게 되고 결국 binary cross entropy로 사용이 가능하다.**   


## Code description
*code상에서, encoder의 output이 mean & log_var인가?*   
encoder의 마지막 layer의 activation function이 없기 때문에, value range는 [-무한대, +무한대]   
반면, 표준편차(sigma)는 0보다 커야 하므로 (표준편차 = 분산의 제곱근)   
log(표준편차의 제곱)이 output이라고 가정하고 진행한다.   
이후, loss computation을 보면 exp(0.5*log_var)로 simga로 다시 계산한 뒤 reparameterization trick을 적용하는 걸 볼 수 있다.   
