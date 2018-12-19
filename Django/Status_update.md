# Employee Status Applicaton in Inventory

There will be different log in for different users and every one has to fill the status form, to updte their status to the manager.

1.Here is how I represented the models related to the user types:
from django.contrib.auth.models import AbstractUser
from django.db import models

class User(AbstractUser):
    is_employee = models.BooleanField(default=False)
    is_manager = models.BooleanField(default=False)

class Employee(models.Model):
    user = models.OneToOneField(User, on_delete=models.CASCADE, primary_key=True)
    status = models.ManyToManyField(Quiz, through='TakenQuiz')
    interests = models.ManyToManyField(Subject, related_name='interested_employees')

2.I created one sign up view and form for each case.
urls.py

from django.urls import include, path

from classroom.views import classroom, students, teachers

urlpatterns = [
    path('', include('team.urls')),
    path('accounts/', include('django.contrib.auth.urls')),
    path('accounts/signup/', classroom.SignUpView.as_view(), name='signup'),
    path('accounts/signup/employee/', students.employeeSignUpView.as_view(), name='employee_signup'),
    path('accounts/signup/manager/', teachers.managerSignUpView.as_view(), name='manager_signup'),
]

3. Employee signup:

from django.contrib.auth import login
from django.shortcuts import redirect
from django.views.generic import CreateView

from ..forms import employeeSignUpForm
from ..models import User

class employeeSignUpView(CreateView):
    model = User
    form_class = employeeSignUpForm
    template_name = 'registration/signup_form.html'

    def get_context_data(self, **kwargs):
        kwargs['user_type'] = 'employee'
        return super().get_context_data(**kwargs)

    def form_valid(self, form):
        user = form.save()
        login(self.request, user)
        return redirect('employee:quiz_list')

4.We need to create signup
5.next step is to protect the views(Explained in decorators.py)
6.Verifying User Type(Explained in templates/base.html)