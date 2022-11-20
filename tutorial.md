
### What are web components?
Web Components is a bunch of different technologies bundeled together allowing the user to create reusable custom elements with their functionalities, which later on can be re-used and utilized in your web apps.

### [Svelte](https://svelte.dev/)

Svelte is a modern JavaScript framework used to build static web applications. Users use Svelte to build reusable components for any type of projects.

One of the main reason svelte is used in developing our [weblets](https://play.grid.tf/#/) is components can be used as standalone packages that work anywhere.

## To build your own weblet, you need to:
- Choose your own solution
- Prepare the docker image
- Prepare the Flist
- Create a a weblet
- Set the solution provider
- test against the grid

### 1. Choose your own solution
The solution we're choosing is going to be [pasty](https://github.com/lus/pasty) which is a fast and lightweight code pasting server. So let's check it.
1. Clone the repository:
```bash
git clone https://github.com/lus/pasty
```
2. Switch to specified directory
```bash 
cd pasty/
```
3. Build the application
```bash
go build -o pasty ./cmd/pasty/main.go
```


### 2. Prepare a docker image 
[Docker](https://www.docker.com/) packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime.


In our case, Pasty already has a Dockerfile in its repository. We need to add some minor changes to the Dockerfile.

1. We need to add a directory to save the code pastes to
```bash
RUN mkdir ./file_name/
```
2. We need to create a new image in ubuntu based image that supports ssh server and run our pasty image in it.

You can run the image using
```bash
docker run -d \
    -p 8080:8080 \
    --name pasty \
    -e PASTY_AUTODELETE="true" \
    -e PASTY_STORAGE_FILE_PATH="file_name"
    image-name
```


After that push the image to docker hub
```bash
docker push image-name
```

### 3. Prepare the flist

At this stage we need to convert our image into an flist. Navigate to [Zero-Os Hub](https://hub.grid.tf/) and login to your account. After that navigate to the docker tab and enter the image's name to convert it an flist. When it's converted it's going to be saved in your repository in the contributers section.

### 4. Create your own weblet
We'll be using svelte and typescript to build our own web application.

### 5.Set the solution provider

### 6. Test against the grid