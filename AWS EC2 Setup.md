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
  <a href="#readme-top"><img src="path-to-your-image" alt="Back to top"></a>
</div>
<h2 id="system-setup">System Setup</h2>
<p>Follow the steps below to prepare your system for development.</p>
<h3 id="update-system-packages">Update System Packages</h3>
<p>Start by updating your system’s package list to ensure all packages are up to date:</p>
<pre><code class="language-bash">sudo apt update
</code></pre>
<h3 id="nodejs-installation">Node.js Installation</h3>
<p>Install the latest LTS version of Node.js using the following commands:</p>
<pre><code class="language-bash">curl -fsSL https://deb.nodesource.com/setup_lts.x | sudo -E bash -
sudo apt-get install -y nodejs
</code></pre>
<p>Verify the installation:</p>
<pre><code class="language-bash">node --version
</code></pre>
<h3 id="nvm-installation">NVM Installation</h3>
<p>Install NVM (Node Version Manager) to manage Node.js versions:</p>
<pre><code class="language-bash">curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
</code></pre>
<p>After the script finishes, apply the changes:</p>
<pre><code class="language-bash">source ~/.bashrc
</code></pre>
<p>Verify NVM installation:</p>
<pre><code class="language-bash">nvm --version
</code></pre>
<p>Install the latest version of Node.js using NVM:</p>
<pre><code class="language-bash">nvm install node
</code></pre>
<h3 id="pm2-installation">PM2 Installation</h3>
<p>Install PM2, a process manager for Node.js applications:</p>
<pre><code class="language-bash">npm install pm2 -g
</code></pre>
<p>Verify PM2 installation:</p>
<pre><code class="language-bash">pm2 --version
</code></pre>
<h3 id="google-chrome-installation">Google Chrome Installation</h3>
<p>Install Google Chrome by following these steps:</p>
<ol>
  <li>
    <p>Install dependencies required for Google Chrome:</p>
    <pre><code class="language-bash">sudo apt install -y wget apt-transport-https ca-certificates curl</code></pre>
  </li>
  <li>
    <p>Download the Google Chrome .deb package:</p>
    <pre><code class="language-bash">wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb</code></pre>
  </li>
  <li>
    <p>Install Google Chrome:</p>
    <pre><code class="language-bash">sudo dpkg -i google-chrome-stable_current_amd64.deb</code></pre>
  </li>
  <li>
    <p>If there are dependency issues, resolve them with:</p>
    <pre><code class="language-bash">sudo apt-get -f install</code></pre>
  </li>
  <li>
    <p>Verify the installation:</p>
    <pre><code class="language-bash">google-chrome --version</code></pre>
  </li>
  <li>
    <p>To locate the installation path:</p>
    <pre><code class="language-bash">which google-chrome</code></pre>
  </li>
</ol>
<h3 id="yarn-installation">Yarn Installation</h3>
<p>Install Yarn, a package manager, by following these steps:</p>
<ol>
  <li>
    <p>Add the Yarn repository key:</p>
    <pre><code class="language-bash">curl -sS https://dl.yarnpkg.com/debian/pubkey.gpg | sudo apt-key add -</code></pre>
  </li>
  <li>
    <p>Add the Yarn repository to your system’s package sources:</p>
    <pre><code class="language-bash">echo "deb https://dl.yarnpkg.com/debian/ stable main" | sudo tee /etc/apt/sources.list.d/yarn.list</code></pre>
  </li>
  <li>
    <p>Update your package index:</p>
    <pre><code class="language-bash">sudo apt update</code></pre>
  </li>
  <li>
    <p>Install Yarn:</p>
    <pre><code class="language-bash">sudo apt install yarn</code></pre>
  </li>
</ol>

