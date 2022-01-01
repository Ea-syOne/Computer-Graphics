## Transformation
점들의 집합을 옮기는 것. Object의 이동이나 조정에 사용된다. 
### Linear Transformation
행렬 곱을 통해 Transformation을 표현하는 것. <br>
행렬의 곱으로 점의 이동을 표현하는 식은 T(v) = Mv로, 이는 
1. T(u + v) = T(u) + T(v)가 성립하고, 
2. T(αv) = αT(v)가 성립하기 때문에 선형성을 갖는다고 할 수 있다. 

##### Linear Transformation & Canonical Basis Vector
Linear Transformation에서 곱해지는 행렬의 각 행은 현재 object의 Canonical Basis Vector와 같다.<br>
즉 2차원에서는 [ 1 0 | 0 1 ]의 identify Matrix에서 x축의 Canonical Basis Vector는 (1,0), y축의 Canonical Basis Vector는 (0,1)이다.<br>
따라서 x축에 영향을 주고자 하면 0번 행 (1,0)에, y축에 영향을 주고자 하면 1번 행 (0,1)에 원하는 Transformation에 따른 규칙에 따른 변화 값을 주게 된다. 
##### Scale
기존의 Object를 확대/축소하는 Trans. Identity Matrix에서 각 축에 원하는 배율 si만큼 곱한 행렬을 사용한다.<br>
2차원의 경우 [ s0 0 | 0 s1 ]와 같다. 이때 s0과 s1이 다른 경우를 non-uniform Scale, 같은 경우를 Uniform Scale이라 한다.
##### Rotation
기존 Object를 회전시키는 Trans. θ만큼 회전할 경우 [ cosθ -sinθ | sinθ cosθ ]를 vector에 곱해준다.<br>
각 Canonical Basis Vector인 (1,0), (0,1)을 θ만큼 회전할 경우 가리키는 방향이 위와 같기 때문.
##### Reflection
기존 Object의 좌우를 뒤집는 Trans. Identity Matrix에서 뒤집고자 하는 축의 1 값을 -1로 뒤집은 행렬을 사용한다. 
##### Shear
기존 Object를 기울이는 Trans. Object를 x축 방향으로 a * y만큼 밀고 싶을 때 [1  a | 0 1 ] 행렬을 곱하게 된다. 
#### Translation(=> Not Linear Transformation)
Vector를 평행이동하는 Trans.를 Translation이라 한다. Translation은 vector 합으로 표현되는데, 이는 Linear Transformation으로는 표현이 불가능하다.

### Affine Transformation
Linear Transformation과 Translation의 합성, T(v) = Mv + u 로 이루어진 Transformation이다. 
#### Rigid Transformation
Affine Transformation 중에서 Linear Transformation에 사용하는 Matrix를 Rotation Matrix만을 사용하는 Transformation을 의미한다. <br>
Rigid Transformation의 특징으로는 형태와 크기를 유지한 채 위치와 방향만을 바꾼다는 점이 있다.

### Composing Transformation
여러개의 변환을 순서대로 적용시켜서 원하는 하나의 변환을 이루는 방식의 Transformation을 의미한다. Linear Transformation의 경우 크기를 2배 키우고 회전시키고 싶을 때 T(P) = M(scale) * M(rotate) * P와 같이 행렬 곱으로 나타낼 수 있다.  <br>
문제는 Affine Transformation일 경우인데, 이 경우 Linear와 동일하게 단순한 곱으로 구현할 수 없다는 문제가 있다. 

### Homogeneous Coordinates
기존의 N차원 Vector와 Transformation을 N+1차원 Vector와 Matrix로 표현한다는 개념. 기존의 Vector (x,y)를 (x,y,**w**)로 표현하고, 2차원 Transformation은 **extra row/column**을 붙여 3 * 3 Matrix로 표현한다. **w**의 경우 1 값을 넣고, **extra row/column**의 경우 translation을 표현하는 데에 사용한다. 
*  **w=1인 이유**: 값이 1이면 실제 x, y 계산에 영향을 미치지 않기 때문.
*  **extra column이 translation을 나타내는 이유**: x축을 나타내는 행의 extra column에 값 t를 넣을 경우, w=1과 계산되면서 기존 벡터 x값을 x+t로 변환시킨다. 이는 x축으로 t만큼 translation한 것과 같은 계산 결과이다.

따라서 Affine Transformation에서 T(p) = M(T) * p + u(T)와 같이 Transformation한 것을 T(p) = [ M(T) u(T) | 0 1 ]과 같이 하나의 행렬로 나타낼 수 있게 되고, 이는 여러 Transformation을 Compose 할 시 단순한 행렬 곱으로 나타낼 수 있게 됨을 의미한다.
