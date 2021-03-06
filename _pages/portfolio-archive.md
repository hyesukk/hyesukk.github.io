---
title: "Portfolio"
layout: single
permalink: /portfolio/
---

<h3>Tech Stack.</h3>
<ul>
    <li>P​rogramming language
        <ul>
            <li>C, C++, Python, Shell</li>
        </ul>
    </li>
    <li>​SCM
        <ul>
            <li>GitLab, Git</li>
        </ul>
    </li>
    <li>​DevOps
        <ul>
            <li>GitLab CI, Jenkins</li>
        </ul>
    </li>
</ul>

<h3>Experience</h3>
<table>
    <tr>
        <th> Time </th>
        <th> Title </th>
        <th> Company </th>
    </tr>
    <tr>
        <td>
            2021.07 ~ current
        </td>
        <td>
            <a href="https://www.ahnlab.com/kr/site/product/productView.do?prodSeq=135">CAL Developer</a> 
        </td>
        <td>
            <a href="https://www.ahnlab.com/kr/site/main.do"> Ahnlab</a>
        </td>
    </tr>
    <tr>
        <td>
            2015.04 ~ 2021.06
        </td>
        <td>
            <a href="http://wins21.com/product/product_030101.html?num=24">IPS/DDoS</a> Developer
        </td>
        <td>
            <a href="http://wins21.com/main/main.html">WINS</a>
        </td>
    </tr>
    <tr>
        <td>
            2013.03 ~ 2015.02
        </td>
        <td>
            Master's course
        </td>
        <td>
            <a href="http://ailab.kyonggi.ac.kr/">Kyonggi University in AI Lab</a>
        </td>
    </tr>
    <tr>
        <td>
            2009.03 ~ 2013.02
        </td>
        <td>
            Student
        </td>
        <td>
            <a href="http://www.kyonggi.ac.kr/KyonggiUp.kgu">Kyonggi University</a>
        </td>
    </tr>
</table>

<h3>Projects</h3>
<table>
    <tr>
        <th> Time </th>
        <th> Company </th>
        <th> Title </th>
        <th> Skills </th>
    </tr>
    {% for portfolio in site.portfolio reversed %}

    {% if portfolio.categories contains "project" and portfolio.categories.size == 1 %}
    <tr>
        <td>{{ portfolio.time }}</td>
        <td>{{ portfolio.company }}</td>
        <td>
            {% assign content = portfolio.content | strip_newlines %}
            {% if content != ""  or portfolio.redirect_to %}
                <a href="{{ portfolio.url }}">{{ portfolio.title }}</a>
            {% else %}
                {{ portfolio.title }}
            {% endif %}
        </td>        
        <td>{{ portfolio.skills | join: ", " }}</td>
    </tr>
    {% endif %}
    {% endfor %}
</table>

<h3>Personal Projects(Including Student)</h3>
<table>
    <tr>
        <th> Time </th>
        <th> Title </th>
        <th> Skills </th>
    </tr>
    {% for portfolio in site.portfolio reversed %}

    {% if portfolio.categories contains "personal" %}
    <tr>
        <td>{{ portfolio.time }}</td>
        <td>
            {% assign content = portfolio.content | strip_newlines %}
            {% if content != ""  or portfolio.redirect_to %}
                <a href="{{ portfolio.url }}">{{ portfolio.title }}</a>
            {% else %}
                {{ portfolio.title }}
            {% endif %}
        </td>        
        <td>{{ portfolio.skills | join: ", " }}</td>
    </tr>
    {% endif %}
    {% endfor %}
</table>

<h3>Education</h3>
<ul>
    <li>2013 ~ 2015, Master student in AI Lab at University of Kyonggi (<a href="http://ailab.kyonggi.ac.kr/">AI Lab</a>)</li>
    <li>2009 ~ 2013, Computer Sience at University of Kyonggi, Suwon, Korea.</li>
</ul>

<table>
    <tr><td>
        <b>[Master Thesis]</b>
        <a href="http://www.riss.kr/link?id=T13732536">Effective Activity Recognition with Probabilistic Graphical Model Learning
.</a>
        Master Thesis. University of Kyonggi, 2015.02
    </td></tr>
</table>
