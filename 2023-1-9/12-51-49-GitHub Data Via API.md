## USER
I want to create an awesome github list with links to interesting github projects. But I want to include with each link information, like: [stars], [last commit date], etc. 

## ASSISTANT
There are a few different ways you can include this information in a list of GitHub projects:

1. You can use GitHub's REST API to fetch data about specific repositories, including the number of stars and the date of the last commit. You can then use this data to generate a list with the desired information.

2. You can use GitHub's GraphQL API to fetch the same data. This is a more powerful and flexible option, but it does require a bit more work to set up.

3. You can use a third-party tool or service that provides an interface for fetching repository data. For example, there are a number of websites that allow you to search for repositories and display their metadata, including the number of stars and the date of the last commit.

Regardless of which approach you choose, you'll need to have some programming skills to be able to retrieve and display the data you're interested in. If you're not comfortable with programming, you might consider asking for help from someone who is.

## USER
I should write a shell script that outputs an MD file, or html? What useful information can I get about a public project?

## ASSISTANT
You can choose to output either an MD (Markdown) file or an HTML file, depending on what you prefer. Both of these formats are widely used for formatting text documents, and they are both supported by GitHub.

As for the information you can get about a public project, there is a wide range of data available through the GitHub API. Here are a few examples of the types of data you might be interested in:

- Repository metadata: This includes information like the repository name, description, creation date, and last update date.

- Contributor data: You can get information about the users who have contributed to the repository, including their names and the number of contributions they have made.

- Issue and pull request data: You can get information about open and closed issues and pull requests, including the number of open issues, the number of closed issues, and the number of open pull requests.

- License information: If the repository has a license, you can get information about the type of license and the terms of use.

This is just a small sample of the data that is available. You can find a full list of the data that is available through the GitHub API in the documentation. 

## USER
Can you get the size in bytes of someone elses public repo?

## ASSISTANT
Yes, you can get the size of someone else's public repository using the GitHub API. Specifically, you can use the `Repository` type in the GraphQL API to query for the `diskUsage` field. This field returns the total disk usage of the repository in bytes.

Here is an example GraphQL query that retrieves the disk usage of a repository:

```
{
  repository(name: "repo-name", owner: "owner-name") {
    diskUsage
  }
}
```

Keep in mind that you will need to have an access token with the `repo` scope in order to query for repository data using the GraphQL API. You can find more information about authenticating with the API and the different types of access tokens in the documentation.

## USER
Can you do it in the rest API?

## ASSISTANT
Yes, you can also retrieve the size of a repository using the GitHub REST API. To do this, you can send a `GET` request to the `/repos/{owner}/{repo}` endpoint, where `{owner}` is the username of the repository owner and `{repo}` is the name of the repository.

The response to this request will include a `size` field, which represents the size of the repository in kilobytes. For example:

```
{
  "id": 12345678,
  "name": "repo-name",
  "full_name": "owner-name/repo-name",
  "size": 42,
  ...
}
```

You can find more information about this endpoint and the data it returns in the documentation for the REST API.


## USER
Now write a complete shell script that takes a URL as input, and outputs the following:
* Repo Name
* Link
* Last Commit Date
* Size
So that I can include that in the README.MD file of my awesome github collection project.

## ASSISTANT
Here is a shell script that takes a URL as input and outputs the repository name, link, last commit date, and size using the GitHub REST API:

```
#!/bin/bash

# Set the base URL for the API
base_url=https://api.github.com

# Extract the owner and repo name from the URL
repo_url=$1
repo_name=$(echo $repo_url | sed 's/.*\///')
owner=$(echo $repo_url | sed 's/https:\/\/github.com\///' | sed 's/\/.*//')

# Query the API for repository data
response=$(curl -s "$base_url/repos/$owner/$repo_name")

# Extract the data we want from the response
name=$(echo $response | jq -r '.name')
url=$(echo $response | jq -r '.html_url')
last_commit_date=$(echo $response | jq -r '.pushed_at')
size=$(echo $response | jq -r '.size')

# Output the data
echo "Repo Name: $name"
echo "Link: $url"
echo "Last Commit Date: $last_commit_date"
echo "Size: $size kb"
```

To use this script, save it to a file and make it executable, then run it with the URL of the repository as the argument. For example:

```
./repo-info.sh https://github.com/owner-name/repo-name
```

This script makes use of the `jq` tool to parse the JSON response from the API and extract the data we want. You will need to have `jq` installed in order to use this script. You can find more information about `jq` and how to install it on the jq website.

I hope this helps! Let me know if you have any questions.

## USER
Great! Now how can I add that output to the readme.md, so it that it looks pretty on my project?

## ASSISTANT
To include the output of the shell script in your `README.md` file, you can simply copy and paste the output into the file. Here is an example of how the output might look in the file:

```
## My Awesome GitHub Project Collection

Here is a list of some interesting GitHub projects I've found:

- **Repo Name**: [Link](url)  
  *Last Commit Date:* date  
  *Size:* size kb

- **Another Repo**: [Link](url)  
  *Last Commit Date:* date  
  *Size:* size kb

...
```

To make the output look nice and readable in the file, you can use Markdown formatting to add headings, lists, and other formatting elements. For example, you can use asterisks to create bullet points, and you can use square brackets and parentheses to create links.

You can find more information about Markdown formatting in the documentation for GitHub Flavored Markdown. This is a variant of Markdown that is used by GitHub and includes additional features and syntax for formatting text.

## USER
Would it look better in html? I want each result to be pretty. Like this:
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
Yes, you can use HTML to create a more visually appealing layout for the list of repository information in your `README.md` file. Here is an example of how you might do this using the HTML code you provided as a reference:

```html
<!-- Repository list -->
<ul>
  <li class="repo-item">
    <!-- Repository name -->
    <h3 class="repo-name">
      <a href="url">Repo Name</a>
    </h3>
    <!-- Repository link -->
    <a href="url" class="repo-link">Link</a>
    <!-- Last commit date -->
    <p class="last-commit-date">Last Commit Date: date</p>
    <!-- Size -->
    <p class="size">Size: size kb</p>
  </li>
  <!-- Repeat for additional repositories -->
</ul>
```

To include this HTML in your `README.md` file, you can simply copy and paste it into the file. You will need to replace the placeholder text (e.g. `Repo Name`, `date`, `size`) with the actual data retrieved from the repository using the shell script.

You can use CSS styles to further customize the appearance of the list and the individual repository items. For example, you might want to add some padding or margins to create more space between the items, or you might want to change the font size or color of the text. You can define your styles in a separate `style` element or in a separate CSS file and link to it in the `head` of your HTML document.

I hope this helps! Let me know if you have any questions.

## USER
Do I need to use a README.md, or can I use a real html page instead?

## ASSISTANT
You can use either a `README.md` file or a separate HTML page to display the list of repository information in your project.

A `README.md` file is a common way to provide information about a project on GitHub, as it is easily readable and can be rendered directly on the project's homepage. `README.md` files use Markdown formatting, which is a simple way to format text using plain text characters.

If you prefer to use a more fully-featured HTML page, you can create a separate HTML file and include it in your project. This will allow you to use more advanced HTML features and styles to create a more visually appealing layout for the list of repository information.

Regardless of which option you choose, you will need to include the HTML or Markdown file in your project's repository and ensure that it is properly linked from the project's homepage or other relevant pages. You can do this by committing the file to the repository and pushing the changes to GitHub, or by uploading the file to the repository using the GitHub web interface.

I hope this helps! Let me know if you have any questions.