---
share: true
title: Spells
---

<script>
/** Patches a mkdoc page in order  some section levels to be foldable (i.e., collapsable).
 * - Usage: 
 *    - Include this file at the end of each concerned `.md` file and adapt the last line to your usage.
 * - Notice: The make_foldable() function is called at the bottom of this file.
 * - Disclaimer: This is only a small hack, use it as it !
 * @param upper_level The upper section level to be made foldable.
 * @param lower_level The lower section level to be made foldable.
 * - For instance, `make_foldable(2, 4)` makes `<H2>`, `<H3>`, and `<H4>` entitled sections foldable.
 * @copyright [CeCILL-C](https://cecill.info/licences/Licence_CeCILL-C_V1-en.html), in brief: Please, use it at will :)
 */
function make_foldable(upper_level = 2, lower_level = 4) { 
  // Applies on the <article> part of the body
  var body = document.getElementsByTagName("article")[0], index = 0;
  // Recursively defines the foldable hierachy
  function do_foldable_contents(parent, hlevel) {
    // Iterates on body childs remainder
    while(index < body.childNodes.length) {
      let item = body.childNodes[index++], tagName = item.tagName;
      // Calculates the section level
      const hTagNameRegExp = new RegExp("^H([1-9])$");
      if (tagName != undefined && tagName.match(hTagNameRegExp)) {
	let level = parseInt(tagName.replace(hTagNameRegExp, "$1"));
	// Returns if detecting an upper section
	if (level <= hlevel) {
	  index--;
	  break;
	}
	// Detects a section to make foldable
	if (upper_level <= level && level <= lower_level) {
	  // Creates a <details><summary> structure
	  let detailsElement = document.createElement("details");
	  if (hlevel == 0)
	    parent.replaceChild(detailsElement, body.childNodes[index]);
	  else
	    parent.appendChild(detailsElement);
	  detailsElement.setAttribute("class", tagName);
	  let summaryElement = document.createElement("summary");
	  summaryElement.appendChild(item);
	  detailsElement.appendChild(summaryElement);
	  do_foldable_contents(detailsElement, level);
	  continue;
	} 
      }
      // Otherwise ... copy the element to the embbeded structure
      if (hlevel > 0) {
	parent.appendChild(item);
      }
    }
  }
  // Starts the iterative foldation :) on the article body
  do_foldable_contents(body, 0);
}
// Here we only want <h3> sections to be foldable.
make_foldable(3, 3);</script>

This page lists the various spells into tables, organized by affinity. Some spells may fall under multiple categories for affinity. Details of the spell and related talents are located on their individual pages.

## Air (Essence) Affinity Spells

| Name                                 | Keywords                       |
| ------------------------------------ | ------------------------------ |
| [Air Geyser](Air Geyser)             | Maneuver, Evocation            |
| [Alter Winds](Alter Winds)           | Evocation                      |
| [Call Lightning](Call Lightning)     | Electric, Evocation            |
| [Concussive Shout](Concussive Shout) | Force, Shaped, Maneuver, Sonic |
| [Slow Fall](Slow Fall)               | Force, Transmutation           |

### Cold (Fire-Anima) Affinity Spells

| Name | Keywords |
| ---- | -------- |


## Decay (Nature-Anima) Affinity Spells

| Name | Keywords |
| ---- | -------- |

## Earth (Water-Anima) Affinity Spells

| Name | Keywords |
| ---- | -------- |

## Fire (Essence) Affinity Spells

| Name | Keywords |
| ---- | -------- |


## Nature(Essence) Affinity Spells

| Name | Keywords |
| ---- | -------- |

## Void (Air-Anima) Affinity Spells

| Name                   | Keywords             |
| ---------------------- | -------------------- |
| [Slow Fall](Slow Fall) | Force, Transmutation |

## Water (Essence) Affinity Spells

| Name | Keywords |
| ---- | -------- |

## Any/Other

Any spells are spells designed to utilize any affinity talent, usually for the purposes of damage type; otherwise it is for spells that have no affinity and rather have their affinity determined by talents chosen.

| Name | Keywords |
| ---- | -------- |
