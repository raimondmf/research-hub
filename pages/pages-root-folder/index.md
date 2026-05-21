---
#
# Use the widgets beneath and the content will be
# inserted automagically in the webpage. To make
# this work, you have to use › layout: frontpage
#
layout: frontpage
header:
  image_fullwidth: header_unsplash_12.jpg
widget1:
  title: "AI Governance Framework"
  url: '/ai-governance/'
  image: widget-1-302x182.jpg
  text: 'A comprehensive control matrix mapping agentic tool security against international standards: NIST AI RMF, ISO 42001, OWASP Agentic Security, Google SAIF, and MITRE ATLAS.'
widget2:
  title: "Tabletop Exercises"
  url: '/tabletop/'
  image: widget-github-303x182.jpg
  text: 'Scenario-based exercises for security teams to practice incident response, test playbooks, and build muscle memory for AI-related security events.'
widget3:
  title: "Cyber Hygiene"
  url: '/cyber-hygiene/'
  image: header_unsplash_5.jpg
  text: 'Practical blueprints for improving security maturity across organizations — from data classification to DLP scanning and shared responsibility models.'
widget4:
  title: "AI API Security"
  url: '/api-security/'
  image: header_unsplash_7.jpg
  text: 'Security guidance for teams building and consuming AI APIs — covering authentication, rate limiting, prompt injection defenses, and data handling best practices.'
#
# Use the call for action to show a button on the frontpage
#
# To make internal links, just use a permalink like this
# url: /getting-started/
#
# To style the button in different colors, use no value
# to use the main color or success, alert or secondary.
# To change colors see sass/_01_settings_colors.scss
#
callforaction:
  url: https://github.com/raimondmf/research-hub
  text: View on GitHub ›
  style: alert
permalink: /index.html
#
# This is a nasty hack to make the navigation highlight
# this page as active in the topbar navigation
#
homepage: true
---
