---  
layout: default  
title: "Curriculum Vitae of Dr Richard Matthews"  
---  
  
<!-- Begin: Resume Content -->  
<div id="resume-content">  
<div id="top"></div>
  
<h1>{{ page.title }}</h1>  
<!-- Print / PDF Controls (Top) -->
<div class="no-print cv-actions" id="cv-actions-top">
  <button type="button" class="cv-btn" onclick="window.print()">Print / Save as PDF (recommended)</button>
  <button type="button" class="cv-btn" id="download-pdf" disabled title="PDF download is loading…">Download PDF (beta)</button>
</div>
  
<!-- Personal Information -->  
<div class="cv-personal-info">  
  <h2>{{ site.data.personal_information.full_name }}</h2>  
  <h3>{{ site.data.personal_information.professional_titles | join: ', ' }}</h3>  
  <p>Location: {{ site.data.personal_information.location }}</p>  
</div>  
  
<!-- Professional Summary -->  
<p>{{ site.data.personal_information.professional_summary }}</p>  
  
<hr class="cv-separator">
  
<!-- Table of Contents -->  
<nav class="cv-toc">
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
  
<hr class="cv-separator">
  
<!-- Education -->  
<section id="education">
  <h2>Education</h2>
  {% assign education_list = site.data.education.education | default: site.data.education %}
  {% if education_list and education_list.size > 0 %}
  {% for education in education_list %}
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
  {% else %}
    <p class="cv-empty">No education entries found (check _cvdata/education.json structure).</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
<!-- Research Employment -->  
<section id="research-employment">
  <h2>Research Employment</h2>
  {% assign positions_list = site.data.experience.positions | default: site.data.experience %}
  {% if positions_list and positions_list.size > 0 %}
  {% for position in positions_list %}
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
  {% else %}
    <p class="cv-empty">No research employment entries found (check _cvdata/experience.json structure).</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
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
  
<hr class="cv-separator">
  
<!-- Awards and Prizes -->  
<section id="awards-and-prizes">
  <h2>Awards and Prizes</h2>
  {% assign awards_list = site.data.awards_prizes.awards | default: site.data.awards_prizes %}
  {% if awards_list and awards_list.size > 0 %}
  <ul>
    {% for award in awards_list %}
      <li>  
        {{ award.year }}: {{ award.award }}  
        {% if award.description %}  
          - {{ award.description }}  
        {% endif %}  
      </li>  
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No awards listed.</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
<!-- Research Motivation -->  
<section id="research-motivation">
  <h2>Research Motivation</h2>  
  <p>{{ site.data.research_motivation.motivation | markdownify }}</p>  
</section>  
  
<hr class="cv-separator">
  
<!-- Publications -->  
<section id="publications">
  <h2>Publications</h2>
  <p>Last updated: {{ site.data.activity.last_updated | default: '2026-01-20' }}</p>
  {% assign activity_href = site.data.activity.activity_link %}
  {% unless activity_href contains '://' %}
    {% assign activity_href = activity_href | prepend: '/' %}
  {% endunless %}
  <p>To see my publication activity including citations as a graph please <a href="{{ site.baseurl }}{{ activity_href }}">click here</a>.</p>

  <h3>Journals</h3>
  {% assign journals_list = site.data.journals.journals | default: site.data.journals %}
  {% if journals_list and journals_list.size > 0 %}
  <ul>
    {% for journal in journals_list %}
      <li>
        {{ journal.authors | join: ', ' }}. {{ journal.year }}. "<em>{{ journal.title }}</em>". <strong>{{ journal.journal }}</strong>.
        {% if journal.volume %} Vol. {{ journal.volume }},{% endif %}
        {% if journal.pages %} pp. {{ journal.pages }},{% endif %}
        {% if journal.month %} {{ journal.month }},{% endif %}
        {% if journal.doi %}
          {% assign doi_href = journal.doi_link | default: journal.link %}
          {% if doi_href %}
            {% unless doi_href contains '://' %}
              {% assign doi_href = doi_href | prepend: 'https://doi.org/' %}
            {% endunless %}
            DOI: <a href="{{ doi_href }}" target="_blank" rel="noopener">{{ journal.doi }}</a>.
          {% else %}
            DOI: {{ journal.doi }}.
          {% endif %}
        {% endif %}
      </li>
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No journals listed.</p>
  {% endif %}

  <h3>Technical and Policy Reports</h3>
  {% assign reports_list = site.data.technical_reports.reports | default: site.data.technical_reports %}
  {% if reports_list and reports_list.size > 0 %}
  <ul>
    {% for report in reports_list %}
      <li>
        {{ report.authors | join: ', ' }}. {{ report.year }}. "<em>{{ report.title }}</em>". {{ report.publisher }}.
        {% if report.location %} {{ report.location }},{% endif %}
        {% if report.link %}
          {% if report.link contains '://' %}
            Available: <a href="{{ report.link }}" target="_blank" rel="noopener">{{ report.link }}</a>.
          {% else %}
            Available: {{ report.link }}.
          {% endif %}
        {% endif %}
      </li>
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No technical/policy reports listed.</p>
  {% endif %}

  <h3>Popular Sources</h3>
  {% assign popular_list = site.data.popular_sources.sources | default: site.data.popular_sources %}
  {% if popular_list and popular_list.size > 0 %}
  <ul>
    {% for source in popular_list %}
      <li>
        {{ source.author }}{% if source.co_author %} and {{ source.co_author }}{% endif %}. ({{ source.year }}). "{{ source.title }}". {{ source.publisher }}.
        {% if source.type %} ({{ source.type }}){% endif %}.
        {% if source.link %}
          {% if source.link contains '://' %}
            Available: <a href="{{ source.link }}" target="_blank" rel="noopener">{{ source.link }}</a>.
          {% else %}
            Available: {{ source.link }}.
          {% endif %}
        {% endif %}
      </li>
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No popular sources listed.</p>
  {% endif %}
</section>
  
<hr class="cv-separator">
  
<!-- Patents and Open Source Deployments -->  
<section id="patents-and-projects">
  <h2>Patents and Open Source Deployments</h2>
  {% assign projects_list = site.data.patents_projects.projects | default: site.data.patents_projects %}
  {% if projects_list and projects_list.size > 0 %}
  {% for project in projects_list %}
    <h3>{{ project.title }}</h3>  
    <p>Date: {{ project.date }}</p>  
    <p>Link: <a href="{{ project.link }}">{{ project.link }}</a></p>  
    <p>{{ project.description | markdownify }}</p>  
  {% endfor %}
  {% else %}
    <p class="cv-empty">No patents/projects listed.</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
<!-- Funding -->  
<section id="funding">
  <h2>Funding</h2>  
  
  <h3>Grants</h3>  
  <ul>  
    {% for grant in site.data.funding.grants %}  
      <li>  
        {% if grant.investigator %}  
          {{ grant.investigator }}  
        {% else %}  
          {{ grant.investigators | join: ', ' }}  
        {% endif %}.  
        {{ grant.year }}. "{{ grant.title }}". {{ grant.funder }}. {{ grant.amount }}.  
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
  
<hr class="cv-separator">
  
<!-- Conference Proceedings and Abstracts -->  
<section id="conference-proceedings">
  <h2>Conference Proceedings and Abstracts</h2>
  {% assign proceedings_list = site.data.conference_proceedings.proceedings | default: site.data.conference_proceedings %}
  {% if proceedings_list and proceedings_list.size > 0 %}
  <ul>
    {% for proceeding in proceedings_list %}
      <li>  
        {{ proceeding.authors | join: ', ' }}. {{ proceeding.year }}. "<em>{{ proceeding.title }}</em>". In {{ proceeding.conference }}. {{ proceeding.location }}.  
        {% if proceeding.link %}
          {% if proceeding.link contains '://' %}
            Available: <a href="{{ proceeding.link }}" target="_blank" rel="noopener">{{ proceeding.link }}</a>.
          {% else %}
            Available: {{ proceeding.link }}.
          {% endif %}
        {% endif %}
      </li>  
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No conference proceedings listed.</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
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
  
<hr class="cv-separator">
  
<!-- Academic Service -->  
<section id="academic-service">
  <h2>Academic Service</h2>
  {% assign services_list = site.data.academic_service.services | default: site.data.academic_service %}
  {% if services_list and services_list.size > 0 %}
  <ul>
    {% for service in services_list %}
      <li>  
        {{ service.role }}  
        {% if service.event %} for {{ service.event }}{% endif %}  
        {% if service.organization %} at {{ service.organization }}{% endif %}  
        {% if service.start_year %} ({{ service.start_year }} - {{ service.end_year }}){% endif %}  
        {% if service.link %} <a href="{{ service.link }}" target="_blank" rel="noopener">Link</a>{% endif %}  
      </li>  
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No academic service entries listed.</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
<!-- Expert Memberships -->  
<section id="expert-memberships">
  <h2>Expert Memberships</h2>
  {% assign memberships_list = site.data.expert_memberships.memberships | default: site.data.expert_memberships %}
  {% if memberships_list and memberships_list.size > 0 %}
  <ul>
    {% for membership in memberships_list %}
      <li>  
        {{ membership.organization }}  
        {% if membership.start_year %} ({{ membership.start_year }} - {{ membership.end_year }}){% endif %}  
        {% if membership.note %} - {{ membership.note }}{% endif %}  
      </li>  
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No expert memberships listed.</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
<!-- Expert Witness -->  
<section id="expert-witness">
  <h2>Expert Witness</h2>  
  <p>{{ site.data.expert_witness.intro | markdownify }}</p>  
  
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
  
<hr class="cv-separator">
  
<!-- Continued Training -->  
<section id="continued-training">
  <h2>Continued Training</h2>
  {% assign trainings_list = site.data.continued_training.trainings | default: site.data.continued_training %}
  {% if trainings_list and trainings_list.size > 0 %}
  <ul>
    {% for training in trainings_list %}
      <li>  
        {{ training.course }}. {{ training.provider }}. {{ training.year }}.  
      </li>  
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No continued training entries listed.</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
<!-- Member Bodies -->  
<section id="member-bodies">
  <h2>Member Bodies</h2>
  <p>Dr Matthews has made a commitment to the profession as a member of the following bodies:</p>
  {% assign bodies_list = site.data.member_bodies.bodies | default: site.data.member_bodies %}
  {% if bodies_list and bodies_list.size > 0 %}
  <ul>
    {% for body in bodies_list %}
      <li>  
        {{ body.organization }}  
        {% if body.status %} ({{ body.status }}){% endif %}  
      </li>  
    {% endfor %}
  </ul>
  {% else %}
    <p class="cv-empty">No member bodies listed.</p>
  {% endif %}
</section>  
  
<hr class="cv-separator">
  
<!-- References -->  
<section id="references">
  <h2>References</h2>  
  <p>{{ site.data.references.note }}</p>  
</section>

<hr class="cv-separator">

<p><a href="#top">Back to Top</a></p>
  
</div><!-- End of #resume-content div -->  
  
<!-- Print / PDF Controls (Bottom) -->
<div class="no-print cv-actions" id="cv-actions-bottom">
  <button type="button" class="cv-btn" onclick="window.print()">Print / Save as PDF (recommended)</button>
  <button type="button" class="cv-btn" id="download-pdf-bottom" disabled title="PDF download is loading…">Download PDF (beta)</button>
</div>

<!-- Include html2pdf.js Library (CDN). Consider vendoring locally later. -->
<script src="https://cdnjs.cloudflare.com/ajax/libs/html2pdf.js/0.9.3/html2pdf.bundle.min.js" defer></script>

<!-- JavaScript for PDF Generation -->
<script>
(function () {
  function wire(btn) {
    if (!btn) return;
    btn.addEventListener('click', function () {
      if (typeof html2pdf === 'undefined') {
        alert('PDF download is unavailable (html2pdf failed to load). Use Print / Save as PDF instead.');
        return;
      }
      const element = document.getElementById('resume-content');
      if (!element) {
        alert('Could not find resume content to export.');
        return;
      }

      const opt = {
        margin:      [10, 10, 10, 10],
        filename:    'Richard_Matthews_CV.pdf',
        image:       { type: 'jpeg', quality: 0.98 },
        html2canvas: { scale: 2 },
        jsPDF:       { unit: 'mm', format: 'a4', orientation: 'portrait' }
      };

      const original = btn.textContent;
      btn.disabled = true;
      btn.textContent = 'Generating…';

      element.classList.add('print-pdf');

      html2pdf().set(opt).from(element).save()
        .catch(function (err) {
          console.error(err);
          alert('PDF generation failed. Use Print / Save as PDF instead.');
        })
        .finally(function () {
          element.classList.remove('print-pdf');
          btn.disabled = false;
          btn.textContent = original;
        });
    });
  }

  function enableButtons() {
    const topBtn = document.getElementById('download-pdf');
    const botBtn = document.getElementById('download-pdf-bottom');

    const available = (typeof html2pdf !== 'undefined');
    [topBtn, botBtn].forEach(function (b) {
      if (!b) return;
      b.disabled = !available;
      b.title = available ? '' : 'PDF download unavailable; use Print / Save as PDF.';
      wire(b);
    });
  }

  if (document.readyState === 'loading') {
    document.addEventListener('DOMContentLoaded', function () { setTimeout(enableButtons, 0); });
  } else {
    setTimeout(enableButtons, 0);
  }
})();
</script>