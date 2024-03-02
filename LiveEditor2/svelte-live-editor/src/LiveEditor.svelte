<script>
    import { Editor, EditorContent } from 'svelte-tiptap';
    import  StarterKit  from '@tiptap/starter-kit';
    import { marked } from 'marked'; // For Markdown to HTML

  
    // Initial content for the editor
    // let initialContent = `
    // <div>
    //   <h2>Hello from Tiptap!</h2>
    //   <p>This is a <strong>simple</strong> example of integrating Tiptap with Svelte.</p>
    // </div>
    // `;

    let initialMarkdownContent = "# hello this is a live editor! \n This is a **Markdown** example";
    let initialHTMLContent = marked(initialMarkdownContent)
  
    // Editor options
    const test = new Editor({
      extensions: [
        StarterKit,
      ],
      content: initialHTMLContent
    });
  </script>
  
  <main>
    <EditorContent editor = {test} />
  </main>
  
  <style>
    /* You might want to add some styles for your editor */
    main {
      max-width: 800px;
      margin: 40px auto;
      padding: 20px;
      box-shadow: 0 0 10px rgba(0,0,0,0.1);
    }
  </style>
  