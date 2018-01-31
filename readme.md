<h3>Bootstrap Vue Form Components</h3>
<p>this components based on <a href="https://getbootstrap.com">Bootstrap</a>

<h5>Field Component</h5>
<p>Props</p>
<ul>
  <li>fieldType - type of input, default: text</li>
  <li>fieldValue - value of input</li>
  <li>fixedNumber - if fieldType is 'number', count of signs after decimal point</li>
  <li>formType - type of form (form, inline, horizontal), default: 'form'</li>
  <li>label - text in label field</li>
  <li>minNumber - if fieldType is number, minimum value in field</li>
  <li>stepNumber - if fieldType is number, step of change value in field</li>
  <li></li>
  <li>Mark field if value changed</li>
</ul>
<p>Events</p>
<ul>
  <li>on value change - generate event is 'changeValue'</li>
  <li>if fieldType is 'button' on click - generate event is 'clickButton'</li>
</ul>

<h5>Select Component</h5>
<p>Props</p>
<ul>
  <li>typeForm - type of form (form, inline, horizontal), default: 'form'</li>
  <li>options - array of objects to visual map</li>
  <li>label - text in label field</li>
  <li>selectedID - selected option in options array</li>
  <li></li>
  <li>Mark field if value changed</li>
</ul>
<p>Events</p>
<ul>
  <li>on change selected option - generate event is 'changeOption'</li>
</ul>
