VTG movement 구현에 성공하였음.
1. VTG size와 movement설정
-현재 진행중
-background에 임의로 설정한 moving region과 movingObject의 크기, interpolation zone 이 서로 적당한 거리에 있는지, hole과의 거리와 interpolation cell layers(thickness)가 충분하거나 너무 과하지 않는지
(interpolated는 3개 layer), pump dimension과 background hole과의 공차(offset)이 딱 맞을 필요까지는 없음.
2. water depth와 probe location 설정
3. k-epsilon value가 적절한지 tuning
4. mesh 세세하게.. y+ value control (velocity와 cell length 재설정)

VTG spec
Diameter: 1.2m
delta s: 0.305(fixed)
hc(height): 0.725m

water depth: 1.03~1.27m

.dat
// (time ((xTrans yTrans zTrans) (xRot yRot zRot)))  // 주석은 파일 내에 포함되지 않아야 함