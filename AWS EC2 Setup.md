---


---

<h2 id="table-of-contents">Table of Contents</h2>
<ul>
<li><a href="#system-setup">System Setup</a>
<ul>
<li><a href="#update-system-packages">Update System Packages</a></li>
<li><a href="#nodejs-installation">Node.js Installation</a></li>
<li><a href="#nvm-installation">NVM Installation</a></li>
<li><a href="#pm2-installation">PM2 Installation</a></li>
<li><a href="#google-chrome-installation">Google Chrome Installation</a></li>
<li><a href="#yarn-installation">Yarn Installation</a></li>
</ul>
</li>
</ul>
<div align="right">
</div><p><a href="#readme-top"><img src="#table-of-contents" alt=""></a></p>

<h2 id="system-setup">System Setup</h2>
<p>Follow the steps below to prepare your system for development.</p>
<h3 id="update-system-packages">Update System Packages</h3>
<p>Start by updating your system’s package list to ensure all packages are up to date:</p>
<pre><code>sudo apt update
</code></pre>
<h3 id="node.js-installation">Node.js Installation</h3>
<p>Install the latest LTS version of Node.js using the following commands:</p>
<pre><code>curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs 
</code></pre>
<p>Verify the installation:</p>
<pre><code>node --version
</code></pre>
<h3 id="nvm-installation">NVM Installation</h3>
<p>Install NVM (Node Version Manager) to manage Node.js versions:</p>
<pre><code>curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
</code></pre>
<p>After the script finishes, apply the changes:</p>
<pre><code>source ~/.bashrc
</code></pre>
<p>Verify NVM installation:</p>
<pre><code>nvm --version
</code></pre>
<p>Install the latest version of Node.js using NVM:</p>
<pre><code>nvm install node
</code></pre>
<h3 id="pm2-installation">PM2 Installation</h3>
<p>Install PM2, a process manager for Node.js applications:</p>
<pre><code>npm install pm2 -g
</code></pre>
<p>Verify PM2 installation:</p>
<pre><code>pm2 --version
</code></pre>
<h3 id="google-chrome-installation">Google Chrome Installation</h3>
<p>Install Google Chrome by following these steps:</p>
<ol>
<li>
<p>Install dependencies required for Google Chrome:</p>
<p>sudo apt install -y wget apt-transport-https ca-certificates curl</p>
</li>
<li>
<p>Download the Google Chrome .deb package:</p>
<p><code>wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb</code></p>
</li>
<li>
<p>Install Google Chrome:</p>
<p><code>sudo dpkg -i google-chrome-stable_current_amd64.deb</code></p>
</li>
<li>
<p>If there are dependency issues, resolve them with:</p>
<p><code>sudo apt-get -f install</code></p>
</li>
<li>
<p>Verify the installation:</p>
<p><code>google-chrome --version</code></p>
</li>
<li>
<p>To locate the installation path:</p>
<p><code>which google-chrome</code></p>
</li>
</ol>
<h3 id="yarn-installation">Yarn Installation</h3>
<p>Install Yarn, a package manager, by following these steps:</p>
<ol>
<li>
<p>Add the Yarn repository key:</p>
<p><code>curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -</code></p>
</li>
<li>
<p>Add the Yarn repository to your system’s package sources:</p>
<p><code>echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list</code></p>
</li>
<li>
<p>Update your package index:</p>
<p><code>sudo apt update</code></p>
</li>
<li>
<p>Install Yarn:</p>
<p>sudo apt install yarn</p>
</li>
</ol>

