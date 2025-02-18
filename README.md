VTG movement 구현에 성공하였음.
1. VTG size와 movement설정
-현재 진행중
-background에 임의로 설정한 moving region과 movingObject의 크기, interpolation zone 이 서로 적당한 거리에 있는지, hole과의 거리와 interpolation cell layers(thickness)가 충분하거나 너무 과하지 않는지
(interpolated는 3개 layer), pump dimension과 background hole과의 공차(offset)이 딱 맞을 필요까지는 없음.
-테스트 해 본 결과, movingObject의 blockMesh 생성된 영역 안 Hole과의 거리는 사전 정의된 movingObject와 3개 이상의 셀을 두어야 함.(거리는 상관없음) 3개 미만으로 hole을 만들 경우 solver가 작동을 못함.
-overinterdymfoam solver의 dynamic motion과 openfoam의 알고리즘상 탐지되고 설정되는 overset-interpolation 과의 충돌이 발생하는것으로 보임.
2. water depth와 probe location 설정
3. k-epsilon value가 적절한지 tuning
<<<<<<< HEAD
4. mesh 세세하게.. y+ value control (velocity와 cell length 재설정)

VTG spec
Diameter: 1.2m
delta s: 0.305(fixed)
hc(height): 0.725m

water depth: 1.03~1.27m

.dat
// (time ((xTrans yTrans zTrans) (xRot yRot zRot)))  // 주석은 파일 내에 포함되지 않아야 함

test
=======
4. Turbulence model설정 시 model마다 tuning parameter 살펴봐야함.
5. mesh 세세하게.. y+ value control (velocity와 cell length 재설정)
6. setFields 후 moving object의 cellType이 viewer상 제대로 탐지가 안되거나 생성이 안 되는 경우, /movingObject/fvScheme 의 oversetInterpolation-inverseDistance-searchboxDimension의 영역과 크기를 조절하면 해결가능.(box의 크기가 너무 크면 deltaT마다 탐색하는 범위가 커지고 iteration이 느려짐. 안정적인 계산을 위해서 dynamic motion에서 움직이는 전체 범위를 커버하는것도 나쁘지 않음.

7. 
>>>>>>> 5d7d8974587f51d36b53026e3adc4534796c19f4
