# challenge-2410-park
## 로컬 구동 방법

1. **git clone **
   ```bash
   git clone https://github.com/thelisn/challenge-2410-park.git
   ```

2. ** npm install **
   ```bash
   npm install
   ```

3. ** env 값 추가 **
   ```bash
   VITE_SUPABASE_URL=https://<project>.supabase.co
   VITE_SUPABASE_ANON_KEY=<your-anon-key>
   ```
   env 값은 Supabase에 따로 테이블을 만들고, supabase.from("table") >  설정하신 테이블 이름으로 "table" 부분 바꾸시면 됩니다.

4. ** npm run dev **
   ```bash
   npm run dev
   ```

##개발 스택
### [FE]
![Vue.js](https://img.shields.io/badge/vuejs-%2335495e.svg?style=for-the-badge&logo=vuedotjs&logoColor=%234FC08D)

### [BE,DB]
[Supabase](https://supabase.com/)
