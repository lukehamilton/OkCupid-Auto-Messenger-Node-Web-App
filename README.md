# Relationship Bootstrap

<p>A Node.js application for auto-messaging all of your matches on OkCupid. This application is the follow up to my previous
foray into automated online dating, OkCupid_Match_Messenger (Ruby version).</p>

<h3>
<a name="how-do-relationship-bootstrap-and-okcupid-match-messenger-ruby-version-compare" class="anchor" href="#how-do-relationship-bootstrap-and-okcupid-match-messenger-ruby-version-compare"><span class="mini-icon mini-icon-link"></span></a>How do Relationship Bootstrap and OkCupid Match Messenger (Ruby Version) Compare?</h3>

<p>Unlike its predecessor, which was only a command line Ruby script, Relation Bootstrap has a web based user friendly interface
where the user can configure how the application will auto-message others and set filters to specify what type of people the
user woud like to message.</p>

<h3>
<a name="how-does-filtering-work" class="anchor" href="#how-does-filtering-work"><span class="mini-icon mini-icon-link"></span></a>How does filtering work?</h3>

<p>A user can filter whom the application will auto-message by the following dimensions:</p>

<ol>
<li>Match %</li>
<li>Friend %</li>
<li>Enemy %</li>
<li>Who's New</li>
<li>Last Online</li>
<li>Special Blend</li>
<li>Match % &amp; New</li>
<li>Match % &amp; Last Online</li>
<li>Match % &amp; Distance</li>
</ol><h2>
<a name="installation-nodejs--dependencies" class="anchor" href="#installation-nodejs--dependencies"><span class="mini-icon mini-icon-link"></span></a>Installation (Node.js &amp; Dependencies)</h2>

<h3>
<a name="install-nodejs" class="anchor" href="#install-nodejs"><span class="mini-icon mini-icon-link"></span></a>Install Node.js</h3>

<h5>
<a name="use-a-pre-compiled-installer-for-your-operating-system" class="anchor" href="#use-a-pre-compiled-installer-for-your-operating-system"><span class="mini-icon mini-icon-link"></span></a>Use a pre-compiled installer for your operating system</h5>

<p>These can be found at the official Node.js website</p>

<p><a href="http://nodejs.org/">http://nodejs.org/</a></p>

<h5>
<a name="use-the-package-manager-homebrew-osx-only" class="anchor" href="#use-the-package-manager-homebrew-osx-only"><span class="mini-icon mini-icon-link"></span></a>Use the package manager Homebrew (OSX only)</h5>

<p>Install Homebrew</p>

<p><code>/usr/bin/ruby -e "$(/usr/bin/curl -fsSL <a href="https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)">https://raw.github.com/mxcl/homebrew/master/Library/Contributions/install_homebrew.rb)</a>"</code></p>

<p>Install Node.js</p>

<p><code>brew install node</code></p>

<p>Install NPM (Node Package Manager)</p>

<p><code>curl <a href="http://npmjs.org/install.sh">http://npmjs.org/install.sh</a> | sh</code></p>

<h3>
<a name="install-mongodb" class="anchor" href="#install-mongodb"><span class="mini-icon mini-icon-link"></span></a>Install MongoDB</h3>

<p>If you already have Homebrew installed from the previous step it's as easy as...</p>

<p><code>brew install mongodb</code></p>

<h3>
<a name="install-dependencies" class="anchor" href="#install-dependencies"><span class="mini-icon mini-icon-link"></span></a>Install Dependencies</h3>

<h5>
<a name="nodejs-dependencies" class="anchor" href="#nodejs-dependencies"><span class="mini-icon mini-icon-link"></span></a>Node.js Dependencies</h5>

<p>Install required Node packages individually</p>

<p><code>npm install express</code></p>

<p><code>npm install mongoose</code></p>

<p><code>npm install request</code></p>

<p><code>npm install jsdom</code></p>

<p><code>npm install ejs</code></p>

<p><code>npm install stylus</code></p>

<p>Or install them simultanesouly from those specified in package.json. Within the top level directory of the application run</p>

<p><code>npm install</code></p>

<h2>
<a name="quick-start" class="anchor" href="#quick-start"><span class="mini-icon mini-icon-link"></span></a>Quick Start</h2>

<h3>
<a name="create-the-mongodb-database-you-will-use" class="anchor" href="#create-the-mongodb-database-you-will-use"><span class="mini-icon mini-icon-link"></span></a>Create the MongoDB database you will use</h3>

<p>At the Mongo cmd line type:</p>

<p><code>use database_name</code></p>

<p>Where "database_name" represents whatever you named your database earlier</p>

<h3>
<a name="configure-the-application-for-deployment" class="anchor" href="#configure-the-application-for-deployment"><span class="mini-icon mini-icon-link"></span></a>Configure the application for deployment</h3>

<p>Specify the MongoDB database you made earlier in okcupid.js</p>

<p>Add your OkCupid username and password where needed in okcupid.js</p>

<h3>
<a name="start-the-application" class="anchor" href="#start-the-application"><span class="mini-icon mini-icon-link"></span></a>Start The Application</h3>

<p>Spinning up the app's server is as easy as:</p>

<p><code>node app.js</code></p>

<h2>
<a name="more-information" class="anchor" href="#more-information"><span class="mini-icon mini-icon-link"></span></a>More Information</h2>

<p>The application needs an OkCupid authenticity token in order to sucessfully send requests to their servers and receive
content back. Unfortunately this is the only step in the entire process that hasn't been automated yet.</p>

<p>My method for obtaining said auth token is as follows:</p>

<ol>
<li><p>Go to OkCupid.com in a browser capable of viewing the HTTP requests going in and out (I found Firefox / Firebug best for
this process).</p></li>
<li><p>Send a message to anyone on the site and inspect the POST request to <a href="http://www.okcupid.com/mailbox">http://www.okcupid.com/mailbox</a> to find the Form Date,
which looks like this:</p></li>
</ol><p>Form Data (url encoded)</p>

<p>ajax:1
sendmsg:1
r1:okaycupidgrl
subject:
body:hey!
threadid:0
authcode:1%2C0%2C1339917833%2C0x3c555cf6c4f6d5af%3Bb16d35ec40883e324e28d4fed05cce9799216a6b
reply:0
from_profile:1</p>

<ol>
<li>Copy the 'authcode' key and paste it into okcupid.js.</li>
