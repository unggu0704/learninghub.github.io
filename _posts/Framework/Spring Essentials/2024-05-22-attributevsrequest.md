---
title: "@ModelAttribute @RequestParam 차이"
author: 김규형
date: 2024-05-22 06:14:11 +0800
categories: [Framework, Spring Essentials]
tags: [BackEnd, SpringBoot, Spring]
render_with_liquid: true
comments: true
image: 
  path: https://velog.velcdn.com/images/zosungwoo/post/fee02cff-da23-4681-a387-8e810b67480c/image.jpg
---

# @ModelAttribute, @RequestParam

- 로그인 시도시에 `@ModelAttribute("user") User user` 를 별도로 안만들어도 된다?

```jsx
	<div class="login-container" align="center">
	    <h2>로그인</h2>
	    <form action="${root}/login" method="post">
	        <div class="form-group">
	            <label for="id">아이디:</label>
	            <input type="text" id="id" name="id" required>
	        </div>
	        <!-- 사용자의 이름을 숨겨진 필드로 설정 -->
	        <input type="hidden" id="name" name="name" value="김싸피">
	        <div class="form-group">
	            <label for="pass">비밀번호:</label>
	            <input type="password" id="pass" name="pass" required>
	        </div>
	        <div class="form-group">
	            <input type="submit" value="login">
	        </div>
	    </form>
	</div>
```

```jsx
	@PostMapping("/login")
	public String login(HttpSession session, Model model, @ModelAttribute("user") User user) {
		logger.debug("userId : {}" , user.getId());
		
		if (user.getId().equals("ssafy") && user.getPass().equals("1234")) {
			session.setAttribute("user", user);
			return "redirect:/index";
		}
			
		model.addAttribute("msg", "로그인에 실패했습니다.");
		return "/";
	}
```

- 자동으로 User 객체를 만들어준다!
- 단 jsp의 form에서 입력 폼을 같은 인자로 설정해줘야한다!

## **@RequestParam**

- URI에 포함된 매개변수 추출에 사용된다.
- 매개변수를 적절히 추출해서 컨트롤러 내에서 자유롭게 사용 가능

## @**PathVariable**

- `/api/user/{id}` 와 같은 경로에서 id값을 가져온다.
