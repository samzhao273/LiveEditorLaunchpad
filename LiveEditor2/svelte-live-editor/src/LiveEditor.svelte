<script>
  import { Editor, EditorContent } from "svelte-tiptap";
  import StarterKit from "@tiptap/starter-kit";
  import { marked } from "marked"; // For Markdown to HTML
  import { onMount } from "svelte";

  // Initial content for the editor
  // let initialContent = `
  // <div>
  //   <h2>Hello from Tiptap!</h2>
  //   <p>This is a <strong>simple</strong> example of integrating Tiptap with Svelte.</p>
  // </div>
  // `;
  
  // let initialMarkdownContent = "";
  // let initialHTMLContent = "";
  // let test;
  // const proxyUrl = 'https://cors-anywhere.herokuapp.com/';
  // const targetUrl = 'https://example.com/markdown-file.md'; // The URL you want to access
  // fetch(`${proxyUrl}${targetUrl}`)

  // // On mount function to fetch from markdown - not allowing b/c of CORS currently // TODO
  // onMount(async () => {
  //   const response = await fetch(`${proxyUrl}${targetUrl}`);
  //   if (response.ok) {
  //     initialMarkdownContent = await response.text();
  //     initialHTMLContent = marked(initialMarkdownContent);

  //             initialMarkdownContent = await response.text();
  //     initialHTMLContent = marked(initialMarkdownContent);
  //   } else {
  //     console.error('Failed to fetch markdown content');
  //   }
  //   // Editor options
  //   test = new Editor({
  //     extensions: [
  //       StarterKit,
  //     ],
  //     content: initialHTMLContent
  //   });
  // });

  let initialMarkdownContent = "";
  let initialHTMLContent;
  let test;

  onMount(async () => {
    const response = await fetch("./README.md");
    if (response.ok) {
      // If the response is fine, then populate the markdown and html content
      initialMarkdownContent = await response.text();
      initialHTMLContent = marked(initialMarkdownContent);
    } else {
      console.error("Failed to fetch README.md");
    }
    // Properties for new editor
    test = new Editor({
      extensions: [StarterKit],
      content: initialHTMLContent,
    });
  });

</script>

<main>
  <EditorContent editor={test} />
</main>

<style>
  main {
    max-width: 800px;
    margin: 40px auto;
    padding: 20px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  }
</style>
