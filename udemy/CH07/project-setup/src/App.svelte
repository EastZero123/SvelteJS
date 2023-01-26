<script>
  import MeetupGrid from "./Meetups/MeetupGrid.svelte";
  import MeetupItem from "./Meetups/MeetupItem.svelte";
  import Button from "./UI/Button.svelte";
  import Header from "./UI/Header.svelte";
  import TextInput from "./UI/TextInput.svelte";

  let title = "";
  let subtitle = "";
  let address = "";
  let email = "";
  let description = "";
  let imageUrl = "";

  let meetups = [
    {
      id: "m1",
      title: "코딩 스벨트",
      subtitle: "코딩 스벨트 배우기",
      description: "투두리스트 스벨트로 배우기",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Svelte_Logo.svg/1200px-Svelte_Logo.svg.png",
      address: "서울특별시 관악구 관악로28길 56",
      contactEmail: "code@test.com",
    },
    {
      id: "m2",
      title: "코딩 즈벨트",
      subtitle: "코딩 즈벨트 배우기",
      description: "투두리스트 즈벨트로 배우기",
      imageUrl:
        "https://upload.wikimedia.org/wikipedia/commons/thumb/1/1b/Svelte_Logo.svg/1200px-Svelte_Logo.svg.png",
      address: "서울특별시 관악구 관악로28길 56",
      contactEmail: "code@test.com",
    },
  ];

  function addMeetup() {
    const newMeetup = {
      id: Math.random().toString(),
      title: title,
      subtitle: subtitle,
      description: description,
      imageUrl: imageUrl,
      contactEmail: email,
      address: address,
    };

    meetups = [newMeetup, ...meetups];
  }
</script>

<Header />

<main>
  <form on:submit|preventDefault={addMeetup}>
    <TextInput
      id="title"
      label="Title"
      type="text"
      value={title}
      on:input={(e) => (title = e.target.value)}
    />
    <TextInput
      id="subtitle"
      label="Subtitle"
      type="text"
      value={subtitle}
      on:input={(e) => (subtitle = e.target.value)}
    />
    <TextInput
      id="address"
      label="Address"
      type="text"
      value={address}
      on:input={(e) => (address = e.target.value)}
    /><TextInput
      id="imageUrl"
      label="Image URL"
      type="text"
      value={imageUrl}
      on:input={(e) => (imageUrl = e.target.value)}
    />
    <TextInput
      id="email"
      label="E-mail"
      type="email"
      value={email}
      on:input={(e) => (email = e.target.value)}
    />
    <TextInput
      id="description"
      label="Description"
      controlType="textarea"
      value={description}
      on:input={(e) => (description = e.target.value)}
    />
    <Button type="submit" caption="Save" />
  </form>
  <MeetupGrid {meetups} />
</main>

<style>
  main {
    margin-top: 5rem;
  }

  form {
    width: 30rem;
    max-width: 90%;
    margin: auto;
  }
</style>
