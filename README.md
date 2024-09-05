# 🎮 AI기반 이미지 추측 게임 EMOJINIOUS

![logo](/images/logo.png)

# 📃 프로젝트 소개 및 개발배경

- 이모지니어스는 AI 기술과 프롬프트 엔지니어링을 게임을 통해 친숙하게 경험할 수 있도록 개발된 플랫폼입니다.

- 이 프로젝트는 AI와의 상호작용을 자연스럽게 유도하며, 사용자들의 AI 리터러시와 프롬프트 엔지니어링 능력을 향상시키는 것을 목표로 합니다.

- 현대 사회에서 AI 기술은 빠르게 확산되고 있으며, 일상생활에서 그 중요성이 점점 커지고 있으나, AI에 익숙하지 않은 사람들에게는 여전히 복잡하고 이해하기 어려운 분야로 느껴집니다. 이모지니어스는 이러한 장벽을 허물고자, 누구나 쉽게 접근할 수 있는 게임 형식을 통해 AI와의 상호작용을 촉직할 수 있도록 설계되었습니다.

# ⚙️ 개발 환경

- Frontend(React 18.2.0, Vite)
  - Deployment: Vercel
  - Communication: SockJS, STOMP
- Backend(Java 17, Spring Boot 3.3.2, Gradle) - Infrastructure: AWS EC2
  - Data Management: Redis
  - Communication: REST API, WebSocket
  - AI Services: OpenAI(DALL-E3, GPT-4) API
- Scoring Server(Python 3.12.3, FastAPI, Uvicorn)
  - HW & OS: Raspberry Pi 5, Ubuntu Server 24.04 LTS - AI/ML: PyTorch, BERT(bert-kor-base)
- Tools
  - VCS: Git
  - IDEs: IntelliJ IDEA, Visual Studio Code, Vim
  - UI/UX & Graphics/Design: Figma, Adobe Illustrator, Photoshop, Premiere Pro, After Effects
  - Collaboration: Notion, Discord
  - Testing & Monitoring: Postman, Grafana
  - DNS: No-IP

# 🛠️ 시스템 아키텍처

![frame](/images/frame.png)

# ⛳️ 페이지별 기능

### [시작화면]

- 게임시작 시 캐릭터 선택 및 닉네임 입력 페이지가 나타납니다.

![start](/images/start.png)

### [캐릭터 선택 및 닉네임 입력]

- 총 10개의 캐릭터가 있으며, 화살표를 클릭하여 캐릭터를 차례로 볼 수 있습니다. 

![charactor](/images/charactor.png)

### [메인 화면에서의 게스트 초대]

- 방장이 처음 방에 들어가게 되면 나오는 화면입니다.
  - 방장은 초대 버튼을 눌러 사용자들을 초대할 수 있는 링크를 복사할 수 있습니다.
  - 링크는 각각의 방을 구별할 수 있도록, 각각의 session id가 파라미터로 붙은 형식입니다.
  - 게스트가 링크를 통해 입장하게 되면, 캐릭터 선택 및 닉네임 입력을 할 수 있는 페이지가 나오며, 모두 입력한 뒤에는 초대자의 방으로 입장하게 됩니다.

![invite](/images/invite.png)

### [메인 화면]

- 게임은 방장 포함 두 명 이상이 되어야 실행할 수 있습니다.

- 게임 설정 및 채팅이 가능합니다.
  - 게임 설정에는 주제, 난이도, 턴, 프롬프트 입력시간, 정답 입력시간이 포함됩니다. 
  - 설정이나 채팅이 업데이트 되었을 시에는 업데이트 된 부분에 알림이 뜨며, 업데이트 된 사실을 바로 알 수 있습니다.   

![main](/images/main.png)

![mainSetting](/images/mainSetting.png)

### [프롬프트 입력]

- 게임이 시작되면 주제에 맞는 키워드를 AI가 생성하여 각각의 플레이어에게 던져줍니다.

- 이후 플레이어들은 그에 맞는 설명을 시간 안에 입력합니다.

- 입력창 아래에는 타이머가 존재하며, 몇 명이 프롬프트를 제출하였는지 확인할 수 있습니다. 

![prompt](/images/prompt.png)

### [이미지 생성 페이지]

- AI가 프롬프트 입력을 기반으로 이미지를 생성하는 동안 로딩 페이지가 띄어집니다.

![image](/images/image.png)

### [자신의 이미지 확인 및 상대의 이미지 추측]

- 이미지가 생성되면 각각의 플레이어는 자신의 이미지를 먼저 확인합니다.

- 자신의 이미지를 확인한 뒤에는 다른 플레이어의 이미지를 연달아 추측합니다.

![myImage](/images/myImage.png)

![other1](/images/other1.png)

![other2](/images/other2.png)

### [점수 계산 페이지]

- 모두의 추측이 끝나면 점수 계산 로딩 페이지로 이동합니다.

![calcul](/images/calcul.png)


### [턴 결과] 아직 구현X

- 점수 계산이 끝나면 그 턴의 결과가 나타나게 됩니다.
  - 결과 페이지는 플레이어의 수많큼 나타나며, 플레이어의 이미지와 정답을 띄워주고, 각각의 플레이어가 어떤 답을 입력했고 몇 점을 얻었는지 알 수 있습니다.

![middle](/images/middle.png)

### [최종 결과] 아직 구현X

- 만약 턴이 남아있다면 현재 턴의 최종 결과를 본 뒤 다음 턴으로 이동할 수 있습니다.

- 턴이 모두 끝났다면, 한 번 더 플레이하거나 메인 화면으로 돌아갈 수 있습니다. 

![final](/images/final.png)

# ⭐️ 기타

- 키워드 제공 방식
  - GPT-4 모델을 사용하여 테마와 난이도에 따른 한국어 키워드셋을 생성합니다. 생성된 키워드셋은 Redis 캐시에 저장되며, 일주일 동안 유지됩 니다. 캐시된 키워드셋이 있을 경우 새로 생성하지 않고 기존 키워드셋을 사용합니다.
- 이미지 생성 방식
  - DALL-E 3 모델을 사용하여 생성됩니다. 사용자가 제출한 프롬프트를 게임 설정에 따라 정제/변조 후 사용합니다. 생성된 이미지는 1024x1024 픽셀 크 기의 단일 이미지로, 별도의 저장은 하지 않습니다. 생성된 이미지는 일시적 으로 유효한 URL 형태로 제공됩니다.
- 점수 산정 방식
  - kykim/bert-kor-base 모델을 사용하여 정답과 제출한 답의 CLS 토큰 임베 딩 간 코사인 유사도를 계산하고, 이를 백분율로 변환한 후 로그 스케일링 을 적용하여 최종 점수를 산출합니다.
  - score = ((base^similarity_percentage - 1) / (base^100 - 1)) * 100, where base = 1.2
  - 정답을 맞춰서 얻은 점수의 70%를 그림의 주인도 얻게 됩니다. 따라서 다른 사람의 그림을 잘 맞추는 것도 중요하지만, 다른 플레이어들이 내 그림을 맞출 수 있도록 잘 설명하는 것도 중요합니다.
