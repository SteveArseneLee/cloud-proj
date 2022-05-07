config/settings.py의 **INSTALLED_APPS**에
```python
'django.contrib.sites',
'allauth',
'allauth.account',
'allauth.socialaccount',
'allauth.socialaccount.providers.github'
```
추가

**AUTHENTICATION_BACKENDS**에
```python
