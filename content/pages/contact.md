---
title: Contact
hide_title: false
sections:
  - section_id: contact-form
    type: section_form
    content: >
      Hi there! Do you have an idea or need help?. Please fill the contact form
      below or send me an email at  benjamin@bbenitez.tech.
    form_id: contactForm
    form_action: /thank-you
    form_fields:
      - input_type: text
        name: name
        label: Name
        default_value: Your name
        is_required: true
      - input_type: email
        name: email
        label: Email
        default_value: Your email address
        is_required: true
      - input_type: select
        name: subject
        label: Subject
        default_value: Please select
        options:
          - Error on the site
          - Sponsorship
          - Other
      - input_type: textarea
        name: message
        label: Message
        default_value: Your message
      - input_type: checkbox
        name: consent
        label: >-
          I understand that this form is storing my submitted information so I
          can be contacted.
    submit_label: Send Message
seo:
  title: Contact
  description: >-
    Hi there! Do you have an idea or need help?. Please fill the contact form
    below or send me an email at  benjamin@bbenitez.tech.
  extra:
    - name: 'og:type'
      value: website
      keyName: property
    - name: 'og:title'
      value: Contact
      keyName: property
    - name: 'og:description'
      value: >-
        Hi there! Do you have an idea or need help?. Please fill the contact
        form below or send me an email at  benjamin@bbenitez.tech.
      keyName: property
    - name: 'twitter:card'
      value: summary
    - name: 'twitter:title'
      value: Contact
    - name: 'twitter:description'
      value: >-
        Hi there! Do you have an idea or need help?. Please fill the contact
        form below or send me an email at  benjamin@bbenitez.tech.
layout: advanced
---
