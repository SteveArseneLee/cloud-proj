# 해당 내용은 views.py에 들어가는 내용입니다.
일반적인 회원가입
```python
def register(request):
    if request.method == 'GET':
        return render(request, 'register.html')
    elif request.method == 'POST':
        username = request.POST.get('username', None)
        useremail = request.POST.get('useremail', None)
        password = request.POST.get('password',None)
        re_password = request.POST.get('re-password', None)
        
        # if password != re_password:
        #     return HttpResponse('비밀번호가 다릅니다!')
        
        # 에러메시지
        res_data = {}
        if not (username and useremail and password and re_password):
            res_data['error'] = '모든 값을 입력해야합니다'
            
        
        # 비번 다를 경우 에러 메시지
        elif password != re_password:
            # error라는 key 사용
            res_data['error'] = '비밀번호가 다릅니다!'
        else:
            myuser = clouduser(
                username = username,
                useremail = useremail,
                password = make_password(password)
            )
        
            myuser.save()
            
        
        return render(request, 'register.html', res_data)
```