# Bucket
브라우저들에서 스크립트 내에서 초기화 되는 cross-origin HTTP 요청이 제한 되어 일부 CSS가 작업이 안될 수 있음
그럴 경우 **S3-권한-CORS구성**의 ```	<AllowedOrigin></AllowedOrigin>```해당 태그 안에 요청하는 사이트의 주소를 적어준다. 

Ex) 로컬일경우
```
<AllowedOrigin>http://localhost:8000</AllowedOrigin>
```