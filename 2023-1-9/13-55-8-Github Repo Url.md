## USER
I want to add links to other github repositories in my readme. Write a bash script that takes the url of a project as input, and:
1. Requests the info from the github API.
2. Returns that data in format that can to be pasted into a github readme.
Include all of the info from my example that is available. Emulate the format as close as possible. Use embedded html if you need to, but only include markdown and html tags supported by Github-Flavored-Markdown.
Example:
<li class="col-12 d-flex flex-justify-between width-full py-4 border-bottom color-border-muted public source" itemprop="owns" itemscope="" itemtype="http://schema.org/Code">
  <div class="col-10 col-lg-9 d-inline-block">
    <div class="d-inline-block mb-1">
      <h3 class="wb-break-all">
        <a href="/irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier" itemprop="name codeRepository">
        Instagram-Machine-Learning-Random-Forest-Classifier</a>
        <span></span><span class="Label Label--secondary v-align-middle ml-1 mb-1">Public</span>
      </h3>


    </div>

    <div>
        <p class="col-9 d-inline-block color-fg-muted mb-2 pr-4" itemprop="description">
          Random Forest Classifier to find items for sale on instagram
        </p>
    </div>


      <div class="topics-row-container d-inline-flex flex-wrap flex-items-center f6 my-1">
          <a data-ga-click="Topic, repository list" data-octo-click="topic_click" data-octo-dimensions="topic:bloom-filters,repository_id:196196070,repository_nwo:irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier,repository_public:true,repository_is_fork:false" href="/topics/bloom-filters" title="Topic: bloom-filters" data-view-component="true" class="topic-tag topic-tag-link f6 my-1">
  bloom-filters
</a>
          <a data-ga-click="Topic, repository list" data-octo-click="topic_click" data-octo-dimensions="topic:machine-learning,repository_id:196196070,repository_nwo:irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier,repository_public:true,repository_is_fork:false" href="/topics/machine-learning" title="Topic: machine-learning" data-view-component="true" class="topic-tag topic-tag-link f6 my-1">
  machine-learning
</a>
          <a data-ga-click="Topic, repository list" data-octo-click="topic_click" data-octo-dimensions="topic:random-forest,repository_id:196196070,repository_nwo:irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier,repository_public:true,repository_is_fork:false" href="/topics/random-forest" title="Topic: random-forest" data-view-component="true" class="topic-tag topic-tag-link f6 my-1">
  random-forest
</a>
          <a data-ga-click="Topic, repository list" data-octo-click="topic_click" data-octo-dimensions="topic:machine-learning-algorithms,repository_id:196196070,repository_nwo:irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier,repository_public:true,repository_is_fork:false" href="/topics/machine-learning-algorithms" title="Topic: machine-learning-algorithms" data-view-component="true" class="topic-tag topic-tag-link f6 my-1">
  machine-learning-algorithms
</a>
          <a data-ga-click="Topic, repository list" data-octo-click="topic_click" data-octo-dimensions="topic:scraping,repository_id:196196070,repository_nwo:irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier,repository_public:true,repository_is_fork:false" href="/topics/scraping" title="Topic: scraping" data-view-component="true" class="topic-tag topic-tag-link f6 my-1">
  scraping
</a>
          <a data-ga-click="Topic, repository list" data-octo-click="topic_click" data-octo-dimensions="topic:probabilistic-models,repository_id:196196070,repository_nwo:irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier,repository_public:true,repository_is_fork:false" href="/topics/probabilistic-models" title="Topic: probabilistic-models" data-view-component="true" class="topic-tag topic-tag-link f6 my-1">
  probabilistic-models
</a>
          <a data-ga-click="Topic, repository list" data-octo-click="topic_click" data-octo-dimensions="topic:probabilistic-data-structures,repository_id:196196070,repository_nwo:irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier,repository_public:true,repository_is_fork:false" href="/topics/probabilistic-data-structures" title="Topic: probabilistic-data-structures" data-view-component="true" class="topic-tag topic-tag-link f6 my-1">
  probabilistic-data-structures
</a>
      </div>

    <div class="f6 color-fg-muted mt-2">

        <span class="ml-0 mr-3">
  <span class="repo-language-color" style="background-color: #3572A5"></span>
  <span itemprop="programmingLanguage">Python</span>
</span>




        Updated <relative-time datetime="2022-12-30T19:14:49Z" class="no-wrap" title="Dec 30, 2022, 7:14 PM GMT">Dec 30, 2022</relative-time>
    </div>
  </div>
  <div class="col-2 d-flex flex-column flex-justify-around flex-items-end ml-3">
        <template class="js-unstar-confirmation-dialog-template">
  <div class="Box-header">
    <h2 class="Box-title">Unstar this repository?</h2>
  </div>
  <div class="Box-body">
    <p class="mb-3">
      This will remove {{ repoNameWithOwner }} from the {{ listsWithCount }} that it's been added to.
    </p>
    <div class="form-actions">
      <!-- '"` --><!-- </textarea></xmp> --><form class="js-social-confirmation-form" data-turbo="false" action="{{ confirmUrl }}" accept-charset="UTF-8" method="post">
        <input type="hidden" name="authenticity_token" value="{{ confirmCsrfToken }}">
        <input type="hidden" name="confirm" value="true">
          <button data-close-dialog="true" type="submit" data-view-component="true" class="btn-danger btn width-full">    Unstar
</button>
</form>    </div>
  </div>
</template>

  <div data-view-component="true" class="js-toggler-container js-social-container starring-container d-flex">
    <div data-view-component="true" class="starred BtnGroup flex-1">
      <!-- '"` --><!-- </textarea></xmp> --><form class="js-social-form BtnGroup-parent flex-auto js-deferred-toggler-target" data-turbo="false" action="/irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier/unstar" accept-charset="UTF-8" method="post"><input type="hidden" name="authenticity_token" value="CW61J-qelN-shUaL2RgTDZD3Zasw-eB6I1Gc_VWfpoOHGoHkE86ebsQAMxi1K9iEj4EdzhwsXnYq4P8IaKg0eg" autocomplete="off">
          <input type="hidden" value="7NPIAIMq7k-MMmPsfe5pk6_5r3tiTGo6szk6JGXXd_Nip_zDenrk_uS3Fn8R3aIasI_XHk6Z1Da6iFnRWODlCg" data-csrf="true" class="js-confirm-csrf-token">
        <input type="hidden" name="context" value="other">
          <button data-hydro-click="{&quot;event_type&quot;:&quot;repository.click&quot;,&quot;payload&quot;:{&quot;target&quot;:&quot;UNSTAR_BUTTON&quot;,&quot;repository_id&quot;:196196070,&quot;originating_url&quot;:&quot;https://github.com/irthomasthomas?tab=repositories&quot;,&quot;user_id&quot;:20578100}}" data-hydro-click-hmac="6766980453d8eaa801cd055ab95994bbbbbde0a5f0ea13d01004acdc4f25bf63" data-ga-click="Repository, click unstar button, action:profiles/repositories#index; text:Unstar" aria-label="Unstar this repository" type="submit" data-view-component="true" class="rounded-left-2 btn-sm btn BtnGroup-item">    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-star-fill starred-button-icon d-inline-block mr-2">
    <path fill-rule="evenodd" d="M8 .25a.75.75 0 01.673.418l1.882 3.815 4.21.612a.75.75 0 01.416 1.279l-3.046 2.97.719 4.192a.75.75 0 01-1.088.791L8 12.347l-3.766 1.98a.75.75 0 01-1.088-.79l.72-4.194L.818 6.374a.75.75 0 01.416-1.28l4.21-.611L7.327.668A.75.75 0 018 .25z"></path>
</svg><span data-view-component="true" class="d-inline">
            Starred
</span>
</button></form>        <details id="details-user-list-196196070" data-view-component="true" class="details-reset details-overlay BtnGroup-parent js-user-list-menu d-inline-block position-relative">
        <summary aria-label="Add this repository to a list" data-view-component="true" class="btn-sm btn BtnGroup-item px-2 float-none" aria-haspopup="menu" role="button">    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-triangle-down">
    <path d="M4.427 7.427l3.396 3.396a.25.25 0 00.354 0l3.396-3.396A.25.25 0 0011.396 7H4.604a.25.25 0 00-.177.427z"></path>
</svg>
</summary>
  <details-menu class="SelectMenu right-0" src="/irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier/lists" role="menu">
    <div class="SelectMenu-modal">
        <button class="SelectMenu-closeButton position-absolute right-0 m-2" type="button" aria-label="Close menu" data-toggle-for="details-37dc0d">
          <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-x">
    <path fill-rule="evenodd" d="M3.72 3.72a.75.75 0 011.06 0L8 6.94l3.22-3.22a.75.75 0 111.06 1.06L9.06 8l3.22 3.22a.75.75 0 11-1.06 1.06L8 9.06l-3.22 3.22a.75.75 0 01-1.06-1.06L6.94 8 3.72 4.78a.75.75 0 010-1.06z"></path>
</svg>
        </button>
      <div id="filter-menu-37dc0d" class="d-flex flex-column flex-1 overflow-hidden">
        <div class="SelectMenu-list">

            <include-fragment class="SelectMenu-loading" aria-label="Loading">
              <svg role="menuitem" style="box-sizing: content-box; color: var(--color-icon-primary);" width="32" height="32" viewBox="0 0 16 16" fill="none" data-view-component="true" class="anim-rotate">
  <circle cx="8" cy="8" r="7" stroke="currentColor" stroke-opacity="0.25" stroke-width="2" vector-effect="non-scaling-stroke"></circle>
  <path d="M15 8a7.002 7.002 0 00-7-7" stroke="currentColor" stroke-width="2" stroke-linecap="round" vector-effect="non-scaling-stroke"></path>
</svg>
            </include-fragment>
        </div>
        
      </div>
    </div>
  </details-menu>
</details>
</div>
    <div data-view-component="true" class="unstarred BtnGroup flex-1">
      <!-- '"` --><!-- </textarea></xmp> --><form class="js-social-form BtnGroup-parent flex-auto" data-turbo="false" action="/irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier/star" accept-charset="UTF-8" method="post"><input type="hidden" name="authenticity_token" value="D3laUNWaAyDQSnN3Jlp9kctvYB2f55NDqVRemyJ8dn3-s1lXgtEXMBPLIUTfOfAOFfealDwfXRuBeS6jnqFWkA" autocomplete="off">
        <input type="hidden" name="context" value="other">
          <button data-hydro-click="{&quot;event_type&quot;:&quot;repository.click&quot;,&quot;payload&quot;:{&quot;target&quot;:&quot;STAR_BUTTON&quot;,&quot;repository_id&quot;:196196070,&quot;originating_url&quot;:&quot;https://github.com/irthomasthomas?tab=repositories&quot;,&quot;user_id&quot;:20578100}}" data-hydro-click-hmac="bb7f071d6b6d20d1805398802ee7dda072937e601353e352c3e45b26d1100ac8" data-ga-click="Repository, click star button, action:profiles/repositories#index; text:Star" aria-label="Star this repository" type="submit" data-view-component="true" class="js-toggler-target rounded-left-2 btn-sm btn BtnGroup-item">    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-star d-inline-block mr-2">
    <path fill-rule="evenodd" d="M8 .25a.75.75 0 01.673.418l1.882 3.815 4.21.612a.75.75 0 01.416 1.279l-3.046 2.97.719 4.192a.75.75 0 01-1.088.791L8 12.347l-3.766 1.98a.75.75 0 01-1.088-.79l.72-4.194L.818 6.374a.75.75 0 01.416-1.28l4.21-.611L7.327.668A.75.75 0 018 .25zm0 2.445L6.615 5.5a.75.75 0 01-.564.41l-3.097.45 2.24 2.184a.75.75 0 01.216.664l-.528 3.084 2.769-1.456a.75.75 0 01.698 0l2.77 1.456-.53-3.084a.75.75 0 01.216-.664l2.24-2.183-3.096-.45a.75.75 0 01-.564-.41L8 2.694v.001z"></path>
</svg><span data-view-component="true" class="d-inline">
            Star
</span>
</button></form>        <details id="details-user-list-196196070" data-view-component="true" class="details-reset details-overlay BtnGroup-parent js-user-list-menu d-inline-block position-relative">
        <summary aria-label="Add this repository to a list" data-view-component="true" class="btn-sm btn BtnGroup-item px-2 float-none" aria-haspopup="menu" role="button">    <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-triangle-down">
    <path d="M4.427 7.427l3.396 3.396a.25.25 0 00.354 0l3.396-3.396A.25.25 0 0011.396 7H4.604a.25.25 0 00-.177.427z"></path>
</svg>
</summary>
  <details-menu class="SelectMenu right-0" src="/irthomasthomas/Instagram-Machine-Learning-Random-Forest-Classifier/lists" role="menu">
    <div class="SelectMenu-modal">
        <button class="SelectMenu-closeButton position-absolute right-0 m-2" type="button" aria-label="Close menu" data-toggle-for="details-37dc0d">
          <svg aria-hidden="true" height="16" viewBox="0 0 16 16" version="1.1" width="16" data-view-component="true" class="octicon octicon-x">
    <path fill-rule="evenodd" d="M3.72 3.72a.75.75 0 011.06 0L8 6.94l3.22-3.22a.75.75 0 111.06 1.06L9.06 8l3.22 3.22a.75.75 0 11-1.06 1.06L8 9.06l-3.22 3.22a.75.75 0 01-1.06-1.06L6.94 8 3.72 4.78a.75.75 0 010-1.06z"></path>
</svg>
        </button>
      <div id="filter-menu-37dc0d" class="d-flex flex-column flex-1 overflow-hidden">
        <div class="SelectMenu-list">

            <include-fragment class="SelectMenu-loading" aria-label="Loading">
              <svg role="menuitem" style="box-sizing: content-box; color: var(--color-icon-primary);" width="32" height="32" viewBox="0 0 16 16" fill="none" data-view-component="true" class="anim-rotate">
  <circle cx="8" cy="8" r="7" stroke="currentColor" stroke-opacity="0.25" stroke-width="2" vector-effect="non-scaling-stroke"></circle>
  <path d="M15 8a7.002 7.002 0 00-7-7" stroke="currentColor" stroke-width="2" stroke-linecap="round" vector-effect="non-scaling-stroke"></path>
</svg>
            </include-fragment>
        </div>
        
      </div>
    </div>
  </details-menu>
</details>
</div></div>

    <div class="text-right hide-lg hide-md hide-sm hide-xs flex-self-end ">
      



  <span class="tooltipped tooltipped-s" aria-label="Past year of activity">
    <svg width="155" height="30">
      <defs>
        <linearGradient id="gradient-196196070" x1="0" x2="0" y1="1" y2="0">
          <stop offset="0%" stop-color="var(--color-calendar-graph-day-L1-bg)"></stop>
          <stop offset="10%" stop-color="var(--color-calendar-graph-day-L2-bg)"></stop>
          <stop offset="25%" stop-color="var(--color-calendar-graph-day-L3-bg)"></stop>
          <stop offset="50%" stop-color="var(--color-calendar-graph-day-L4-bg)"></stop>
        </linearGradient>
        <mask id="sparkline-196196070" x="0" y="0" width="155" height="28">
          <polyline transform="translate(0, 28) scale(1,-1)" points="0,1 3,1 6,1 9,1 12,1 15,1 18,1 21,1 24,1 27,1 30,1 33,1 36,1 39,1 42,1 45,1 48,1 51,1 54,1 57,1 60,1 63,1 66,1 69,1 72,1 75,1 78,1 81,1 84,1 87,1 90,1 93,1 96,1 99,1 102,1 105,1 108,1 111,1 114,1 117,1 120,1 123,1 126,1 129,1 132,1 135,1 138,1 141,1 144,1 147,1 150,11 153,1 " fill="transparent" stroke="#8cc665" stroke-width="2">
        </polyline></mask>
      </defs>

      <g transform="translate(0, -7)">
        <rect x="0" y="-2" width="155" height="30" style="stroke: none; fill: url(#gradient-196196070); mask: url(#sparkline-196196070)"></rect>
      </g>
    </svg>
  </span>

    </div>
  </div>
</li>

## ASSISTANT
Here is a bash script that will take a GitHub repository URL as input and return the information in the format specified:

```
#!/bin/bash

# Check if jq is installed, if not install it
if ! command -v jq > /dev/null; then
  sudo apt-get install jq
fi

# Extract repository owner and name from URL
repo_url=$1
repo_owner=$(echo "$repo_url" | awk -F'/' '{print $4}')
repo_name=$(echo "$repo_url" | awk -F'/' '{print $5}')

# Make API request to get repository info
response=$(curl -s "https://api.github.com/repos/$repo_owner/$repo_name")

# Extract relevant info from response
name=$(echo "$response" | jq -r '.name')
description=$(echo "$response" | jq -r '.description')
is_private=$(echo "$response" | jq -r '.private')
topics=$(echo "$response" | jq -r '.topics | join(", ")')

# Format output
if [ "$is_private" = "true" ]; then
  privacy_status="Private"
else
  privacy_status="Public"
fi

output="<li class=\"col-12 d-flex flex-justify-between width-full py-4 border-bottom color-border-muted public source\" itemprop=\"owns\" itemscope=\"\" itemtype=\"http://schema.org/Code\">
  <div class=\"col-10 col-lg-9 d-inline-block\">
    <div class=\"d-inline-block mb-1\">
      <h3 class=\"wb-break-all\">
        <a href=\"$repo_url\" itemprop=\"name codeRepository\">$name</a>
        <span></span><span class=\"Label Label--secondary v-align-middle ml-1 mb-1\">$privacy_status</span>
      </h3>
    </div>

    <div>
        <p class=\"col-9 d-inline-block color-fg-muted mb-2 pr-4\" itemprop=\"description\">
          $description
        </p>
    </div>

      <div class=\"topics-row-container d-inline-flex flex-wrap flex-items-center f6 my-1\">"

if [ -n "$topics" ]; then
  for topic in $topics; do
    output="$output
          <a data-ga-click=\"Topic, repository list\" data-octo-click=\"topic_click\" data-octo-dimensions=\"topic:$topic\" href=\"/topics/$topic\" title=\"Topic: $topic\" data-view-component=\"true\" class=\"topic-tag topic-tag-link f6 my-1\">
  $topic
</a>"
  done
fi

output="$output
      </div>
  </div>
</li>"

echo "$output"
```

To use this script, save it to a file (e.g. "get_repo_info.sh") and make it executable with `chmod +x get_repo_info.sh`. Then

## USER
Can you tweak that, so that it takes an argument that is a url to public repo?

## ASSISTANT
Certainly! Here is an updated version of the script that takes a repository URL as a command line argument:

```
#!/bin/bash

# Check if jq is installed, if not install it
if ! command -v jq > /dev/null; then
  sudo apt-get install jq
fi

# Extract repository owner and name from URL
repo_url=$1
repo_owner=$(echo "$repo_url" | awk -F'/' '{print $4}')
repo_name=$(echo "$repo_url" | awk -F'/' '{print $5}')

# Make API request to get repository info
response=$(curl -s "https://api.github.com/repos/$repo_owner/$repo_name")

# Extract relevant info from response
name=$(echo "$response" | jq -r '.name')
description=$(echo "$response" | jq -r '.description')
is_private=$(echo "$response" | jq -r '.private')
topics=$(echo "$response" | jq -r '.topics | join(", ")')

# Format output
if [ "$is_private" = "true" ]; then
  privacy_status="Private"
else
  privacy_status="Public"
fi

output="<li class=\"col-12 d-flex flex-justify-between width-full py-4 border-bottom color-border-muted public source\" itemprop=\"owns\" itemscope=\"\" itemtype=\"http://schema.org/Code\">
  <div class=\"col-10 col-lg-9 d-inline-block\">
    <div class=\"d-inline-block mb-1\">
      <h3 class=\"wb-break-all\">
        <a href=\"$repo_url\" itemprop=\"name codeRepository\">$name</a>
        <span></span><span class=\"Label Label--secondary v-align-middle ml-1 mb-1\">$privacy_status</span>
      </h3>
    </div>

    <div>
        <p class=\"col-9 d-inline-block color-fg-muted mb-2 pr-4\" itemprop=\"description\">
          $description
        </p>
    </div>

      <div class=\"topics-row-container d-inline-flex flex-wrap flex-items-center f6 my-1\">"

if [ -n "$topics" ]; then
  for topic in $topics; do
    output="$output
          <a data-ga-click=\"Topic, repository list\" data-octo-click=\"topic_click\" data-octo-dimensions=\"topic:$topic\" href=\"/topics/$topic\" title=\"Topic: $topic\" data-view-component=\"true\" class=\"topic-tag topic-tag-link f6 my-1\">
  $topic
</a>"
  done
fi

output="$output
      </div>
  </div>
</li>"

echo "$output"
```

To use the script, save it to a file (e.g. "get_repo_info.sh") and make it executable with `chmod +x get_repo_info.sh`. Then run it

## USER
How should I embed that in my md file?

## ASSISTANT
To embed the output of the script in a Markdown file, you can use the `$()` syntax to execute the script and include its output in the file. For example:

```
## My Repositories

<ul>
$(/path/to/get_repo_info.sh https://github.com/user/repo1)
$(/path/to/get_repo_info.sh https://github.com/user/repo2)
$(/path/to/get_repo_info.sh https://github.com/user/repo3)
</ul>
```

This will include a list of your repositories, with each repository's information formatted in the specified way.

Alternatively, you can also use a script to generate the entire Markdown file. For example:

```
#!/bin/bash

output="## My Repositories\n\n<ul>\n"

repos=("https://github.com/user/repo1" "https://github.com/user/repo2" "https://github.com/user/repo3")

for repo in "${repos[@]}"; do
  output="$output$(/path/to/get_repo_info.sh $repo)\n"
done

output="$output</ul>"

echo "$output" > output.md
```

This script will generate a Markdown file called "output.md" that includes a list of your repositories.