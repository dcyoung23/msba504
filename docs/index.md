<h1 class="course-title">{{ course_info().code }}: {{ course_info().title }}</h1>
<h3 class="course-school-term"> {{ course_info().school }}, {{ course_info().term }}</h3>

<a href="{{ course_info().canvas }}"><span class="md-nav-badge md-nav-badge-canvas">Canvas</span></a>
<a href="{{ course_info().gradescope }}"><span class="md-nav-badge md-nav-badge-gradescope">Gradescope</span></a>
<a href="{{ instructor_info().student_hours }}"><span class="md-nav-badge md-nav-badge-calendly">Student Hours</span></a>

![D. Chris Young Profile](assets/images/profile_circle.png){: style="float:left; margin-right:10px; width:150px; height:150px;" }
<br>
<a href="{{ instructor_info().website }}" class="instructor-link">{{ instructor_info().instructor }}</a>  

<br>

### **Course Calendar**

{{ course_calendar_table() }}