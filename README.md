# refactoring

## 1. 기본

### [Extract Method(메서드 추출하기)](src/basic/ExtractMethod.java)

> 코드 조각을 찾아서 무슨 일을 하는지 파악한 다음, 독립된 함수로 추출하고 목적에 맞는 이름을 붙이기

### [Inline Method(메서드 인라인하기)](src/basic/InlineMethod.java)

> 메서드의 본문이 메서드의 명칭 만큼 명확한 경우에는 분리 된 메서드를 인라인한다.

### [Extract Variable(변수 추출하기)](src/basic/ExtractVariable.java)

> 표현식이 너무 복잡해서 이해하기 어려울 때 지역변수를 활용하여 표현식을 쪼개 관리하기 더 쉽게 만든다.
> 현재 함수 안에서만 의미가 있는 값일 때 변수로 추출하고, 함수를 벗어나서 넓은 문맥에서 의미가 있다면 함수로 추출하는것이 좋다.

### [Inline Variable(변수 인라인하기)](src/basic/InlineVariable.java)

> 이름이 원래 표현식과 다를 바 없을 때는 주변 코드를 리팩터링할 때 방해가 될 수 있다. 이럴 때 변수를 인라인한다.

### [Change Method Declaration(메서드 선언 바꾸기)](src/basic/ChangeMethodDeclaration.java)

> 메서드의 이름은 연결부에서 가장 중요한 요소이다. 이름이 좋으면 구현 코드를 보지 않고도 무슨 일을 하는지 명확히 알 수 있다. 매개변수도 마찬가지다.
> 예컨대 전화번호 포매팅 함수가 매개변수로 사람 객체를 받게 된다면, 회사 전화번호에는 사용할 수 없다. 번호 자체를 받도록 정의하면 함수의 활용 범위를 넓힐 수 있다.

### [Encapsulate Variable(변수 캡슐화하기)](src/basic/EncapsulateVariable.java)

> 리팩터링은 결국 프로그램의 요소를 조작하는 일. 메서드는 데이터보다 다루기가 수월하다. 데이터는 메서드보다 다루기가 어려운데, 메서드 선언 바꾸기와 같은 방식으로 전달 메서드를 만들기가 어렵기 때문이다.
> 접근할 수 있는 범위가 넓은 데이터는 데이터를 독점하는 함수를 만드는게 좋다(Getter) 또 데이터를 변경(Setter)하고 사용하는 코드를 감시할 수 있는 확실한 통로가 되어준다. 

### [Introduce Parameter Object(파라미터 객체 만들기)](src/basic/IntroduceParameterObject.java)

> 데이터 항목 여러개가 이 메서드에서 저 메서드로 몰려다니는 경우가 자주 있다. 이런 데이터 구조를 하나로 모아주자. 데이터를 데이터 구조로 묶으면 데이터 관계가 명확해진다.
> 같은 데이터 구조를 사용하는 모든 함수가 원소를 참조할 때 항상 똑같은 이름을 사용하기에 일관성도 높다.

### [Combine Methods Into Class(여러 메서드를 클래스로 묶기)](src/basic/CombineMethodsIntoClass.java)

> 메서드 호출 시 매개변수로 전달되는 공통 데이터를 중심으로 긴밀하게 엮여 작동하는 메서드 목록이 있다면, 클래스 하나로 묶는다. 클래스로 묶으면 이 함수들이 공유하는 공통 환경을 더 명확하게 표현할 수 있다.

### [Combine Methods Into Transform(여러 메서드를 변환 메서드로 묶기)](src/basic/CombineMethodsIntoTransform.java)

> 메서드 호출 시 매개변수로 전달되는 공통 데이터를 중심으로 긴밀하게 엮여 작동하는 메서드 목록이 있다면, 클래스 하나로 묶는다. 클래스로 묶으면 이 함수들이 공유하는 공통 환경을 더 명확하게 표현할 수 있다.


## 2. 캡슐화

### [Encapsulate Record(레코드 캡슐화하기)](src/encapsulate/EncapsulateRecord.java)

> 레코드는 여러가지 데이터를 직관적인 방식으로 묶을 수 있어서 각각을 따로 취급할 때보다 훨씬 의미있는 단위로 전달이 가능하다. 하지만 레코드는 단점이 있다. 계산해서 얻을 수 있는 값과 그렇지 않은 값을 명확히 구분해서 저장해야 한다.
> 이로 인해 레코드보다 객체를 사용하자. 객체를 사용하면 어떻게 저장했는지를 숨긴 채 각각의 메서드로 값을 제공할 수 있다.
 
### [Encapsulate Collection(컬렉션 캡슐화하기)](src/encapsulate/EncapsulateCollection.java)

> 컬렉션을 직접 변경할 수 있으면 눈치채지 못하는 곳에서 컬렉션의 원소들이 바뀔 수 있다. 이러한 문제를 방지하기 위해 컬렉션을 변경하는 메서드를 만든다.

### [Replace Primitive With Object(기본형을 객체로 바꾸기)](src/encapsulate/ReplacePrimitiveWithObject.java)

> 단순한 출력 이상의 기능이 필요해지는 순간 그 데이터를 표현하는 전용 클래스를 정의하자. 나중에 특별한 동작이 필요해지면, 이 클래스에 추가하면 되니 프로그램이 커질수록 점점 유용한 도구가 된다.

### [Replace Temp With Query(임시 변수를 질의 함수로 바꾸기)](src/encapsulate/ReplaceTempWithQuery.java)

> 함수 안에서 어떤 코드의 결과값을 뒤에서 다시 참조할 목적으로 임시 변수를 사용하기도 한다. 임시 변수를 사용하면 값을 계산하는 코드가 반복되는것을 줄일 수 있어서 유용하다.
> 하지만 한걸음 더 나아가 함수로 만들어 사용하는 편이 나을 때가 많다. 변수 대신 함수로 만들어 두면 비슷한 계산을 수행하는 다른 함수에서도 사용할 수 있어 코드 중복이 줄어든다.

### [Extract Class(클래스 추출하기)](src/encapsulate/ExtractClass.java)

> 메서드와 데이터가 너무 많은 클래스는 이해하기가 어려우니 잘 살펴보고 분리하는 것이 좋다. 특히 일부 데이터와 메서드를 따로 묶을 수 있다면 어서 분리하라는 신호다.

### [Inline Class(클래스 인라인하기)](src/encapsulate/InlineClass.java)

> 더 이상 제 역할을 못하는 클래스는 인라인 하자. 역할을 옮기는 리팩터링을 하고 나서 특정 클래스에 남은 역할이 거의 없을 때 이런 현상이 자주 생긴다.
> 두 클래스의 기능을 다르게 분배하고 싶을 때에도 클래스를 인라인 한 이후 다시 추출하면 더 쉬운 경우가 많다.

### [Hide Delegate(위임 숨기기)](src/encapsulate/HideDelegate.java)

> 필드가 가리키는 객체의 메서드를 호출하면, 클라이언트는 위임받은 객체를 알아야 한다. 위임 객체의 인터페이스가 변경되면 이 인터페이스를 사용하는 모든 클라이언트가 코드를 수정해야 한다.
> 이러한 의존성을 없애기 위해 자체에 위임 메서드를 만들어서 위임 객체의 존재를 숨기면, 위임 객체가 수정되어도 객체만 수정하면 각 클라이언트는 영향을 받지 않는다.

### [Remove Middle Man(중개자 제거하기)](src/encapsulate/RemoveMiddleMan.java)

> 클라이언트가 위임 객체의 또 다른 기능을 사용하고 싶을 때마다 객체에 위임 메서드를 추가하게 되면, 단순히 전달만 하는 위임 메서드가 점점 많아진다. 그러다 보면 결국 중개자로 전락하기에 위임 객체를 직접 호출하는 게 나을 수 있다.
> 어느 정도로 숨겨야 할지 트레이드 오프가 필요하다.

### [Substitute Algorithm(알고리즘 교체하기)](src/encapsulate/SubstituteAlgorithm.java)

> 목적을 달성하는 방법은 여러가지가 존재한다. 그 중에서도 다른 것보다 더 쉬운 방법이 존재한다. 알고리즘도 마찬가지다. 더 간명한 방법을 찾아내면 코드를 간명한 방식으로 고친다.
> 리팩터링은 복잡한 대상을 단순한 단위로 나눌 수 있지만, 때로는 알고리즘 전체를 걷어내고 훨씬 간결한 알고리즘으로 바꿔야 할 때가 있다.


## 3. 기능 이동

### [Move Method(메서드 이동하기)](src/move/MoveMethod.java)

> 어떤 함수가 자신이 속한 모듈보다 다른 모듈의 요소를 더 많이 참조한다면, 다른 모듈로 옮겨줘야 마땅하다. 이렇게 하면 캡슐화가 좋아져서, 이 소프트웨어의 나머지 부분은 다른 모듈의 세부사항에 덜 의존한다.
> 비슷하게 호출자들의 현재 위치나 다읍 업데이트에 바뀌리라 예상하는 위치에 따라서도 옮겨줘야 할 수 있다.

### [Move Field(필드 이동하기)](src/move/MoveField.java)

> 현재 데이터 구조가 적합하지 않음을 알게 되면 곧바로 수정하자. 고치지 않고 남은 것들은 추후 머리속을 혼란스럽게 한다.
> 예를 들어 함수에 어떤 레코드를 넘길 때 마다 또 다른 레코드의 필드도 같이 넘기고 있다면, 데이터의 위치를 옮기는것이 좋다.
> 또한 한 레코드를 변경할 때 다른 레코드의 필드도 같이 변경하여야 한다면 필드의 위치가 잘못 되었다는 신호이다.

### [Move Statements Into Method(문장을 메서드로 옮기기)](src/move/MoveStatementsIntoMethod.java)

> 중복 제거는 코드를 건강하게 한다. 이렇게 해두면 추후 반복되는 부분에서 무언가를 수정할 때 단 한곳만 수정하면 된다.

### [Move Statements To Callers(문장을 호출한 곳으로 옮기기)](src/move/MoveStatementsToCallers.java)

> 초기에는 응집도가 높았던 메서드가 어느새 둘 이상의 다른 일을 수행하도록 바뀔 수 있다. 개발자는 동작이 달라진 함수에서 꺼내 해당 호출자로 옮겨줘야 한다.

### [Replace Inline Code With Method Call(인라인 코드를 메서드 호출로 바꾸기)](src/move/ReplaceInlineCodeWithMethodCall.java)

> 메서드는 여러 동작을 하나로 묶는다. 메서드 이름이 코드의 동작 방식보다는 목적을 말해주기 때문에 메서드를 활용하면 코드를 이해하기 쉬워진다. 또한 함수는 중복을 없애는데도 효율적이다.
> 이미 존재하는 메서드와 동일한 일을 하는 인라인 코드를 발견하면 보통은 해당 코드를 메서드 호출로 대체하자. 이름을 잘 지었다면 인라인 코드 대신에 메서드를 넣어도 말이 된다. 이것이 맞지 않다면, 이름이 적절하지 않거나 그 함수의 목적이 다르기 때문 일 것이다.
> 가능하다면 라이브러리가 제공하는 메서드로 대체하는 것이 훨씬 좋다. 메서드 본문조차 작성할 필요가 없다.

### [Slide Statements(문장 슬라이드하기)](src/move/SlideStatements.java)

> 관련된 코드들이 가까이 모여 있으면 이해하기가 더 쉽다. 다른 데이터를 사용하는 사이에 흩어져 있기 보다는 한곳에 모여 있어야 좋다. 함수로 추출하는 리팩터링을 적용하기에 앞서 선행되는 경우가 많다.

### [Split Loop(반복문 쪼개기)](src/move/SplitLoop.java)

> 반복문 하나에서 두가지 일을 수행하는 경우가 종종 있다. 그저 두 일을 한번에 처리할 수 있다는 이유에서 말이다. 이렇게 하면 하나의 반복문을 수정해야 할 때 마다 두가지 일을 모두 잘 이해하고 진행해야 한다.
> 하지만 반복문을 쪼개면 수정할 동작 하나만 이해하면 된다.
> 반복문을 두 번 실행해야 하므로 불편해 하는 프로그래머도 많다. 하지만 리팩토링과 최적화는 구분해야 한다. 최적화를 할 때 리팩토링으로 코드를 깔끔히 정리 한 이후에 최적화를 수행하자. 다시 하나로 합취는건 매우 쉬운 일이다.
> 또한, 반복문을 두번 실행해도 병목현상이 일어나는 경우는 매우 드물다.

### [Replace Loop With Pipeline(반복문을 파이프라인으로 바꾸기)](src/move/ReplaceLoopWithPipeline.java)

> 객체를 순회할 때 반복문을 사용하라고 배웠다. 하지만 언어는 점점 더 나은 구조를 제공하는 쪽으로 발전해왔다. 이번 이야기의 주인공인 컬렉션 파이프라인을 이용하면 처리 과정을 일련의 연산으로 표현할 수 있다.
> 이때 각 연산은 컬렉션을 입력받아 다른 컬렉션을 내뱉는다. 대표적인 연산으로 map, filter가 있다. 
> 논리를 파이프라인으로 표현하면 이해하기가 훨씬 쉬워진다.  
> (Java 8+ 부터 stream API를 지원한다.)

## 4. 데이터 조직화

### [Split Variable(변수 쪼개기)](src/organizing/SplitVariable.java)

> 변수는 다양한 용도로 쓰인다. 그 중 변수에 값을 여러번 대입할 수 밖에 없는 경우도 있다. 예컨데 반복문 안에 있는 루프 변수는 반복문을 한번 돌 때 마다 값이 바뀐다.
> 그 외에도 변수는 긴 코드의 결과를 저장했다가 나중에 쉽게 참조하려는 목적으로 흔히 쓰인다. 이런 변수에는 값을 단 한번만 대입해야 한다. 대입이 두번 이상 이뤄진다면 여러가지 역할을 수행한다는 신호다.
> 역할이 두개 이상 있는 변수는 쪼개야한다. 예외는 없다.  
> (변수는 되도록 불변 상태로 생성하자)

### [Rename Field(필드 이름 바꾸기)](src/organizing/RenameField.java)

> 이름은 중요하다. 특히 프로그램 곳곳에서 쓰이는 레코드 구조체의 이름은 더 중요하다.
> 데이터 구조는 프로그램을 이해하는 큰 역할을 한다. 데이터 구조가 중요한 만큼 반드시 깔끔하게 관리해야 한다.
> 다른 요소와 마찬가지로 개발을 진행할수록 데이터를 더 잘 이해하게 된다. 보다 더 적합한 이름이 생각나면 이름을 바꾸자.

### [Replace Derived Variable With Query(파생 변수를 질의 함수로 바꾸기)](src/organizing/ReplaceDerivedVariableWithQuery.java)

> 가변 데이터는 소프트웨어에 문제를 일으키는 가장 큰 골칫거리에 속한다. 가변 데이터는 서로 다른 두 코드를 이상한 방식으로 결합하기도 한다.
> 가변 데이터를 완전히 배제하기란 불가능하지만, 가변 데이터의 유효 범위를 가능한 좁혀야 한다.
> 효과가 가장 좋은 방법은 값을 쉽게 계산해 낼 수 있는 변수를 모두 제거하자. 계산 과정을 보여주는 코드 자체가 데이터의 의미를 더 분명히 드러내는 경우가 많다.

### [Change Reference To Value(참조를 값으로 바꾸기)](src/organizing/ChangeReferenceToValue.java)

> 객체를 다른 객체에 중첩하면 내부 객체를 참조 호는 값으로 취급할 수 있다.
> 참조냐 값이냐의 차이는 내부 객체의 속성을 갱신하는 방식에서 가장 극명하게 드러난다.
> 참조로 다루는 경우에는 대부 객체는 그대로 둔 채 그 객체의 속성만 갱신하며, 값으로 다루는 경우에는 새로운 속성을 담은 객체로 기존 내부 객체를 통째로 대체한다.
> 필드를 값으로 다룬다면 내부 객체의 클래스를 수정하여 값 객체로 만들 수 있다. 값 객체는 대체로 자유롭게 활용하기 좋다(불변)

### [Change Value To Reference(값을 참조로 바꾸기)](src/organizing/ChangeValueToReference.java)

> 하나의 데이터 구조 안에 논리적으로 똑같은 제 3의 데이터 구조를 참조하는 레코드가 여러개 있을 때가 있다. 이때 데이터를 참조로도, 값으로도 다룰 수 있다.
> 논리적으로 가장 문제가 되는 경우는 그 데이터를 갱신할 때 이다. 모든 복제본을 찾아서 다 갱신해야하며, 하나라도 놓치면 데이터 일관성이 깨진다.
> 이런 상황이라면 데이터를 참조로 관리하는것이 좋다.

### [Replace Magic Literal(매직 리터럴 바꾸기)](src/organizing/ReplaceMagicLiteral.java)

> 매직 리터럴이란 소스코드에 등장하는 일반적인 리터럴 값을 의미한다.
> 예를 들어 움직임을 계산하는 코드라면 9.81이라는 숫자가 산재해 있을 것이다.(표준 중력을 의미함)  
> 하지만 코드를 읽는 사람이 이 의미를 모른다면 숫자 자체로는 명확히 모르므로 매직 리터럴이라 할 수 있다. 코드 자체가 뜻을 분명하게 드러내도록 상수를 정의하고 상수를 사용하도록 바꾸자.

## 5. 조건부 로직 간소화

### [Decompose Conditional(조건문 분해하기)](src/simplifying/DecomposeConditional.java)

> 복잡한 조건부 로직은 프로그램을 복잡하게 만드는 가장 흔한 원흉에 속한다.
> 긴 함수는 그 자체로 읽기도 어렵지만, 조건문은 그 어려움을 한층 더 가중시킨다. 조건을 검사하고 그 결과에 따른 동작을 표현한 코드는 무슨일이 일어나는지는 말해주지만, 왜 일어나는지는 말해주지 않을 때가 많다.
> 거대한 코드 블록이 주어지면 코드를 부위별로 분해 한 다음 코드 덩어리를 각 의도를 살린 함수의 호출로 바꾸자, 무엇을 분기했는지가 명백해진다.

### [Consolidate Conditional Expression(조건식 통합하기)](src/simplifying/ConsolidateConditionalExpression.java)

> 비교하는 조건은 다르지만 그 결과로 수행하는 동작은 똑같은 코드들이 더러 있는데 어차피 같은 일을 할 거라면 조건 검사도 하나로 통합하자.
> 여러 조각으로 나뉜 조건들을 하나로 통합함으로써 내가 하려는 일이 명확해진다.
> 또한, 통합하면 함수 추출하기까지 이어질 가능성이 매우 높다.  
> 하지만, 같은 결과를 반환하더라도 독립적인 비교 조건인 경우 조건식을 통합해서는 안된다.