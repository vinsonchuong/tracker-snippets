# Tracker Snippets
JavaScript snippets for getting more out of Pivotal Tracker

## Usage
These snippets can be run by pasting the code into your browser's JavaScript
console while you have Pivotal Tracker open. Alternatively, you can use
[a service](http://mrcoles.com/bookmarklet/) to generate a bookmarklet for easy
re-use.

Note that many of these snippets will only work when run in Firefox and that
popups need to be enabled for the Pivotal Tracker domain (you will be prompted)
the first time you use a snippet that opens a popup.

## Snippets

### List Stories Owned by a Given User
```js
var personName = window.prompt('What is the full name of the person?');
var project = tracker.Project.current();
var person = project.members().findWhere({name: personName});
var stories = project.stories().filter(function(story) {
  return story.get('owner_ids').indexOf(person.id) >= 0;
});

window.open().document.body.innerHTML = '' +
  '<ul>' +
    stories.map(function(story) {
      return '<li><a href="https://www.pivotaltracker.com/story/show/' + story.id + '">' + story.get('name') + '</a></li>';
    }).join('') +
  '</ul>';
```
