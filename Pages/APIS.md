<p><strong>🃏 APIs</strong><br><br>
<div id="gif-container">
Loading random GIFs...</div><br>
<p>Keywords: 'politics', 'culture', 'intercultural', 'diplomacy'</p>

<script>
  const API_KEY = '7zHjkXzouVQzbfMwzSCYk7e73GglpOlf'; // Replace with your Giphy API key
  const keywords = ['politics', 'culture', 'intercultural', 'diplomacy'];
  const container = document.getElementById('gif-container');

  container.innerHTML = '';

  // Loop through keywords and fetch a random GIF for each
  keywords.forEach(keyword => {
    const url = `https://api.giphy.com/v1/gifs/random?api_key=${API_KEY}&tag=${encodeURIComponent(keyword)}&rating=PG-13`;

    fetch(url)
      .then(res => res.json())
      .then(data => {
        const gifUrl = data.data.images.fixed_height.url;
        // Add each GIF to the container
        const img = document.createElement('img');
        img.src = gifUrl;
        img.alt = keyword + ' GIF';
        container.appendChild(img);
      })
      .catch(err => {
        console.error('Error fetching GIF for', keyword, err);
      });
  });
</script>
