guard :shell do
  watch(/(.*)/) { |m| `git commit -a -m wip`; `git push` }
end
