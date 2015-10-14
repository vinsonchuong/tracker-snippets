# Tracker Snippets
Code snippets you can run from your console

## Listing all of the stories owned by a particular user
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
