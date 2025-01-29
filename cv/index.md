---  
layout: default  
title: Curriculum Vitae of Dr Richard Matthews  
---  
  
<h1>{{ page.title }}</h1>  
  
<!-- Personal Information -->  
<div class="cv-personal-info">  
  <h2>{{ site.data.personal_information.full_name }}</h2>  
  <h3>{{ site.data.personal_information.professional_titles | join: ', ' }}</h3>  
  <p>Location: {{ site.data.personal_information.location }}</p>  
  <p>Email: <span class="obfuscate">{{ site.data.personal_information.email }}</span></p>  
  <p>Phone: <span class="obfuscate">{{ site.data.personal_information.phone }}</span></p>  
</div>  
  
<!-- Professional Summary -->  
<p>{{ site.data.personal_information.professional_summary }}</p>  
  
---  
  
<!-- Table of Contents -->  
<nav>  
  <h2>Contents</h2>  
  <ul>  
    <li><a href="#education">Education</a></li>  
    <li><a href="#research-employment">Research Employment</a></li>  
    <li><a href="#technical-skills">Technical Skills</a></li>  
    <li><a href="#awards-and-prizes">Awards and Prizes</a></li>  
    <li><a href="#research-motivation">Research Motivation</a></li>  
    <li><a href="#publications">Publications</a></li>  
    <li><a href="#patents-and-projects">Patents and Open Source Deployments</a></li>  
    <li><a href="#funding">Funding</a></li>  
    <li><a href="#conference-proceedings">Conference Proceedings and Abstracts</a></li>  
    <li><a href="#teaching-experience">Teaching Experience</a></li>  
    <li><a href="#academic-service">Academic Service</a></li>  
    <li><a href="#expert-memberships">Expert Memberships</a></li>  
    <li><a href="#expert-witness">Expert Witness</a></li>  
    <li><a href="#continued-training">Continued Training</a></li>  
    <li><a href="#member-bodies">Member Bodies</a></li>  
    <li><a href="#references">References</a></li>  
  </ul>  
</nav>  
  
---  
  
<!-- Education -->  
<section id="education">  
  <h2>Education</h2>  
  {% for education in site.data.education %}  
    <h3>{{ education.degree }}</h3>  
    <p>{{ education.institution }}<br>  
    {{ education.location }}<br>  
    {{ education.start_year }} - {{ education.end_year }}</p>  
    {% if education.supervisors %}  
      <p><strong>Supervisors:</strong></p>  
      <ul>  
        {% for supervisor in education.supervisors %}  
          <li>  
            <a href="{{ supervisor.link }}">{{ supervisor.name }}</a> ({{ supervisor.role }})  
          </li>  
        {% endfor %}  
      </ul>  
    {% endif %}  
    {% if education.thesis_title %}  
      <p><strong>Thesis:</strong> <a href="{{ education.thesis_link }}">{{ education.thesis_title }}</a></p>  
    {% endif %}  
    {% if education.electives %}  
      <p><strong>Electives:</strong> {{ education.electives | join: ', ' }}</p>  
    {% endif %}  
    {% if education.honours_thesis %}  
      <p><strong>Honours Thesis:</strong> {{ education.honours_thesis }}</p>  
    {% endif %}  
  {% endfor %}  
</section>  
  
---  
  
<!-- Research Employment -->  
<section id="research-employment">  
  <h2>Research Employment</h2>  
  {% for position in site.data.experience %}  
    <h3>{{ position.position }}</h3>  
    <p>{{ position.employer }}<br>  
    {{ position.location }}<br>  
    {{ position.start_year }} - {{ position.end_year }}</p>  
    <p>{{ position.description | markdownify }}</p>  
    {% if position.publications_generated %}  
      <p><strong>Publications generated:</strong></p>  
      <ul>  
        {% for pub in position.publications_generated %}  
          <li>{{ pub | markdownify }}</li>  
        {% endfor %}  
      </ul>  
    {% endif %}  
  {% endfor %}  
</section>  
  
---  
  
<!-- Technical Skills -->  
<section id="technical-skills">  
  <h2>Technical Skills</h2>  
  <h3>Lab Skills</h3>  
  <ul>  
    {% for skill in site.data.technical_skills.lab_skills %}  
      <li>{{ skill }}</li>  
    {% endfor %}  
  </ul>  
  <h3>Computer Languages and Software Tools</h3>  
  <ul>  
    {% for tool in site.data.technical_skills.computer_languages_and_tools %}  
      <li>{{ tool }}</li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Awards and Prizes -->  
<section id="awards-and-prizes">  
  <h2>Awards and Prizes</h2>  
  <ul>  
    {% for award in site.data.awards_prizes %}  
      <li>  
        {{ award.year }}: {{ award.award }}  
        {% if award.description %}  
          - {{ award.description }}  
        {% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Research Motivation -->  
<section id="research-motivation">  
  <h2>Research Motivation</h2>  
  <p>{{ site.data.research_motivation.motivation | markdownify }}</p>  
</section>  
  
---  
  
<!-- Publications -->    
<section id="publications">    
  <h2>Publications</h2>    
  <p>Last updated: {{ site.data.activity.last_updated }}</p>    
  <p>To see my publication activity including citations as a graph please <a href="{{ site.data.activity.activity_link }}">click here</a>.</p>    
    
  <h3>Journals</h3>    
  <ul>    
    {% for journal in site.data.journals %}    
      <li>    
        {{ journal.authors | join: ', ' }}. {{ journal.year }}. "<em>{{ journal.title }}</em>". <strong>{{ journal.journal }}</strong>.    
        {% if journal.volume %} Vol. {{ journal.volume }},{% endif %}    
        {% if journal.pages %} pp. {{ journal.pages }},{% endif %}    
        {% if journal.month %} {{ journal.month }},{% endif %}    
        DOI: <a href="{{ journal.link }}">{{ journal.doi }}</a>.    
      </li>    
    {% endfor %}    
  </ul>    
    
  <h3>Technical and Policy Reports</h3>    
  <ul>    
    {% for report in site.data.technical_reports %}    
      <li>    
        {{ report.authors | join: ', ' }}. {{ report.year }}. "<em>{{ report.title }}</em>". {{ report.publisher }}.    
        {% if report.location %} {{ report.location }},{% endif %}    
        {% if report.link %} Available: <a href="{{ report.link }}">{{ report.link }}</a>.{% endif %}    
      </li>    
    {% endfor %}    
  </ul>    
    
  <h3>Popular Sources</h3>    
  <ul>    
    {% for source in site.data.popular_sources %}    
      <li>    
        {{ source.author }}{% if source.co_author %} and {{ source.co_author }}{% endif %}. ({{ source.year }}). "{{ source.title }}". {{ source.publisher }}.    
        {% if source.type %} ({{ source.type }}){% endif %}.    
        {% if source.link %} Available: <a href="{{ source.link }}">{{ source.link }}</a>.{% endif %}    
      </li>    
    {% endfor %}    
  </ul>    
</section>     
  
---  
  
<!-- Patents and Open Source Deployments -->  
<section id="patents-and-projects">  
  <h2>Patents and Open Source Deployments</h2>  
  {% for project in site.data.patents_projects %}  
    <h3>{{ project.title }}</h3>  
    <p>Date: {{ project.date }}</p>  
    <p>Link: <a href="{{ project.link }}">{{ project.link }}</a></p>  
    <p>{{ project.description | markdownify }}</p>  
  {% endfor %}  
</section>  
  
---  
  
<!-- Funding -->  
<section id="funding">  
  <h2>Funding</h2>  
  
  <h3>Grants</h3>  
  <ul>  
    {% for grant in site.data.funding.grants %}  
      <li>  
        {{ grant.investigator | default: grant.investigators | join: ', ' }}. {{ grant.year }}. "{{ grant.title }}". {{ grant.funder }}. {{ grant.amount }}.  
      </li>  
    {% endfor %}  
  </ul>  
  
  <h3>Bug Bounties</h3>  
  <ul>  
    {% for bounty in site.data.funding.bug_bounties %}  
      <li>  
        {{ bounty.reporter }}. {{ bounty.year }}. "{{ bounty.title }}". Platform: {{ bounty.platform }}. Amount: {{ bounty.amount }}.  
        {% if bounty.link %} Available: <a href="{{ bounty.link }}">{{ bounty.link }}</a>.{% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Conference Proceedings and Abstracts -->  
<section id="conference-proceedings">  
  <h2>Conference Proceedings and Abstracts</h2>  
  <ul>  
    {% for proceeding in site.data.conference_proceedings %}  
      <li>  
        {{ proceeding.authors | join: ', ' }}. {{ proceeding.year }}. "<em>{{ proceeding.title }}</em>". In {{ proceeding.conference }}. {{ proceeding.location }}.  
        {% if proceeding.link %} Available: <a href="{{ proceeding.link }}">{{ proceeding.link }}</a>.{% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Teaching Experience -->  
<section id="teaching-experience">  
  <h2>Teaching Experience</h2>  
  
  <h3>Academic Appointments</h3>  
  {% for appointment in site.data.teaching_experience.academic_appointments %}  
    <h4>{{ appointment.position }}</h4>  
    <p>{{ appointment.institution }}<br>  
    {{ appointment.start_year }} - {{ appointment.end_year }}</p>  
    <p>{{ appointment.description | markdownify }}</p>  
  {% endfor %}  
  
  <h3>Course Development</h3>  
  {% for course in site.data.teaching_experience.course_development %}  
    <h4>{{ course.course_name }}</h4>  
    <p>{{ course.description | markdownify }}</p>  
  {% endfor %}  
  
  <h3>Research Supervision</h3>  
  {% for supervision in site.data.teaching_experience.research_supervision %}  
    <h4>{{ supervision.role }}</h4>  
    <p>{{ supervision.institution }}<br>  
    {% if supervision.start_year %}{{ supervision.start_year }}{% if supervision.end_year %} - {{ supervision.end_year }}{% endif %}{% endif %}</p>  
    <p>{{ supervision.description | markdownify }}</p>  
  {% endfor %}  
  
  <h3>Teaching Skills</h3>  
  <ul>  
    {% for skill in site.data.teaching_experience.teaching_skills %}  
      <li>{{ skill }}</li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Academic Service -->  
<section id="academic-service">  
  <h2>Academic Service</h2>  
  <ul>  
    {% for service in site.data.academic_service %}  
      <li>  
        {{ service.role }}  
        {% if service.event %} for {{ service.event }}{% endif %}  
        {% if service.organization %} at {{ service.organization }}{% endif %}  
        {% if service.start_year %} ({{ service.start_year }} - {{ service.end_year }}){% endif %}  
        {% if service.link %} [Link]({{ service.link }}){% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Expert Memberships -->  
<section id="expert-memberships">  
  <h2>Expert Memberships</h2>  
  <ul>  
    {% for membership in site.data.expert_memberships %}  
      <li>  
        {{ membership.organization }}  
        {% if membership.start_year %} ({{ membership.start_year }} - {{ membership.end_year }}){% endif %}  
        {% if membership.note %} - {{ membership.note }}{% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Expert Witness -->  
<section id="expert-witness">  
  <h2>Expert Witness</h2>  
  <p>As a prominent forensic scientist, Dr Matthews is sometimes called to act as an expert witness in matters of digital forensics.</p>  
  
  <h3>Expert Witness Cases</h3>  
  <ul>  
    {% for case in site.data.expert_witness.expert_witness_cases %}  
      <li>  
        {{ case.case }} - {{ case.role }}  
      </li>  
    {% endfor %}  
  </ul>  
  
  <h3>Reports Provided</h3>  
  <ul>  
    {% for report in site.data.expert_witness.reports_provided %}  
      <li>  
        {{ report.case }}  
        {% if report.court %} - {{ report.court }}{% endif %}  
        {% if report.year %} ({{ report.year }}){% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
  
  <h3>Advice Provided</h3>  
  <ul>  
    {% for advice in site.data.expert_witness.advice_provided %}  
      <li>  
        {{ advice.case }}  
        {% if advice.agency %} - {{ advice.agency }}{% endif %}  
        {% if advice.location %} in {{ advice.location }}{% endif %}  
        {% if advice.year %} ({{ advice.year }}){% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
  
  <p>{{ site.data.expert_witness.note }}</p>  
</section>  
  
---  
  
<!-- Continued Training -->  
<section id="continued-training">  
  <h2>Continued Training</h2>  
  <ul>  
    {% for training in site.data.continued_training %}  
      <li>  
        {{ training.course }}. {{ training.provider }}. {{ training.year }}.  
      </li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- Member Bodies -->  
<section id="member-bodies">  
  <h2>Member Bodies</h2>  
  <p>Dr Matthews has made a commitment to the profession as a member of the following bodies:</p>  
  <ul>  
    {% for body in site.data.member_bodies %}  
      <li>  
        {{ body.organization }}  
        {% if body.status %} ({{ body.status }}){% endif %}  
      </li>  
    {% endfor %}  
  </ul>  
</section>  
  
---  
  
<!-- References -->  
<section id="references">  
  <h2>References</h2>  
  <p>{{ site.data.references.note }}</p>  
</section>  
  
---  
  
<!-- Back to Top -->  
<p><a href="#top">Back to Top</a></p>  
  