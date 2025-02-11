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

수위는 0.05m 적어도 이하로 표현이 가능해야하고 delta s 도 0.305m 이므로 해당 최소단위인 0.005 크기의 해상도는 갖춰야 함
0.05 크기로 진행했을 때는 계산시간이 대략 3시간 걸렸음


수정할 것들?
1. 수위: 1.00 1.05 1.10 1.15 1.20 1.25 (6개), 프루드 수 조합(Vsp) > spike 발생 시의 vtg 속도... 총 몇 개의 case로 나눈 combination을 만들건지?
2. 위에 명시해둔 VTG spec을 따라서..
3. interFoam 사용 시 spike, 즉 물기둥의 모습을 획득하는데는 한계가 있음.(사실상 interFoam 이 아닌 유한체적법의 한계..) > 일단 geometry 만들고 해당 부분에 단계적인 refinement 수행
4. background의 movement 부분의 불필요하게 넓은 영역 정리
5. 경험상.. spike 관찰을 위해서 양옆 wall의 간격은 VTG 직경의 3배 (3.6m) 정도면 괜찮지 않을까 추측 > 파랑실험장치의 wavelength에 따른 wall과 측정지점에서의 거리 관련 실험 찾아보기
6. wall boundary condition > relaxation zone? 아마 기억상 해당 BC는 waves2Foam library에 속하던것으로 기억...

.dat
// (time ((xTrans yTrans zTrans) (xRot yRot zRot)))  // 주석은 파일 내에 포함되지 않아야 함


