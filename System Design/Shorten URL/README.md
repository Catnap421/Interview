**Problem:** Design a service like TinyURL, a URL shortening service, a web service that provides short aliases for redirection of long URLs. [문제](https://leetcode.com/discuss/interview-question/system-design/124658/Design-URL-Shortening-service-like-TinyURL)

### Answer

short url을 위해서 사용할 수 있는 캐릭터로는 a-z, A-Z, 0-9로 62자다.
unique id를 만들어서, 62자로 인코딩하고 이를 키로 하고 원래의 URL을 밸류로 저장하여 구현한다.
그리고 해당 url로 get 요청이 왔을 때 값을 가져와서 리다이렉트를 시켜주면 된다.

### Feedback

1. 트래픽 볼륨을 고려해야한다. 트래픽 볼륨이 얼마냐에 따라, 62자로 인코딩한 문자열의 길이가 몇이냐에 따라 가질 수 있는 Shorten URL의 수는 정해져 있다. 이를 고려하지 못한 게 아쉽다.
   
2. 단순하게 해시를 통해 매핑을 한다고 했지만, 이 때 충돌을 어떻게 해결할 지 고려하지 못했다. 주어진 url로 부터 id를 만드는 방식은 충돌이 일어날 가능성이 매우 높기 때문에, 단순히 <키, 밸류> 형식으로 저장하는 게 아닌 어울리는 자료구조를 설계해야 한다.
   
3. DB가 단일 클러스터인지 멀티 클러스터 환경인지를 고려해야 한다. 만약 멀티 클러스터일 경우, 어떤 DB를 참조해야하는 지를 알 수 있는 정보가 필요하다.
