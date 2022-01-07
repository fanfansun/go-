# go-
这是 go 语言极简服务器
func main() {
	PORT := ":8085"
	arguments := os.Args
	println("os.Args:", os.Args)
	if len(arguments) == 1 {
		fmt.Println("Using default port number:", PORT)
	} else {
		PORT = ":" + arguments[1]
		fmt.Println("post---/n", arguments)
	}
	// 注册路由
	http.HandleFunc("/time", timeHandler)
	http.HandleFunc("/", serverHandler)

	err := http.ListenAndServe(PORT, nil)
	if err != nil {
		fmt.Println(err)
		return
	}
}

