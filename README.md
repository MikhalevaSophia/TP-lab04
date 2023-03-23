# TP-lab4
> Клонируем репозиторий третьей лабы:
> ```sh
> $ git clone <ссылка на репу третьей лабы>
> $ cd <имя репы третьей лабы>
> $ git remote remove origin
> $ git remote add origin <ссылка на репу четвёртой лабы>
> ```
>
> Создаём директорию `.github/workflows` в директории лабы
>
> В ней создаём файл `CI.yml`:
>
> ```yaml
> name: CMake
> 
> on:
>  push:
>   branches: [main]
>  pull_request:
>   branches: [main]
> 
> jobs: 
>  build_Linux:
> 
>   runs-on: ubuntu-latest
> 
>   steps:
>   - uses: actions/checkout@v3
> 
>   - name: Configure Solver
>     run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build
> 
>   - name: Build Solver
>     run: cmake --build ${{github.workspace}}/solver_application/build
> 
>   - name: Configure HelloWorld
>     run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build
> 
>   - name: Build HelloWorld
>     run: cmake --build ${{github.workspace}}/hello_world_application/build
> 
>  build_Windows:
> 
>   runs-on: windows-latest
> 
>   steps:
>   - uses: actions/checkout@v3
> 
>   - name: Configure Solver
>     run: cmake ${{github.workspace}}/solver_application/ -B ${{github.workspace}}/solver_application/build
> 
>   - name: Build Solver
>     run: cmake --build ${{github.workspace}}/solver_application/build
> 
>   - name: Configure HelloWorld
>     run: cmake ${{github.workspace}}/hello_world_application/ -B ${{github.workspace}}/hello_world_application/build
> 
>   - name: Build HelloWorld
>     run: cmake --build ${{github.workspace}}/hello_world_application/build
> ```
>
> Добавляем файл в проект и пушим на гитхаб:
> ```sh
> $ git add .github
> $ git commit -m "added CI.yml"
> $ git push origin main
> ```
> Заходим на гитхаб, во вкладку **Actions**, и проверяем, что процесс выполнен успешно.
