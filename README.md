# DPVideoMerger-Swift

Step 1:-  Copy & paste DPVideoMerger.swift file into your project 

Step 2:-  Usage 

        import AVKit
        
        let fileURL = Bundle.main.url(forResource: "1", withExtension: "mp4")
        let fileURL1 = Bundle.main.url(forResource: "2", withExtension: "mp4")
        let fileURL2 = Bundle.main.url(forResource: "3", withExtension: "MOV")
        let fileURL3 = Bundle.main.url(forResource: "4", withExtension: "mp4")
        let fileURLs = [fileURL, fileURL1, fileURL2, fileURL3]
        
        DPVideoMerger().mergeVideos(withFileURLs: fileURLs as! [URL], completion: {(_ mergedVideoFile: URL?, _ error: Error?) -> Void in
            if error != nil {
                let errorMessage = "Could not merge videos: \(error?.localizedDescription ?? "error")"
                let alert = UIAlertController(title: "Error", message: errorMessage, preferredStyle: .alert)
                self.present(alert, animated: true) {() -> Void in }
                return
            }
            let objAVPlayerVC = AVPlayerViewController()
            objAVPlayerVC.player = AVPlayer(url: mergedVideoFile!)
            self.present(objAVPlayerVC, animated: true, completion: {() -> Void in
                objAVPlayerVC.player?.play()
            }) 
        })
